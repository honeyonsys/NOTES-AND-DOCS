  

# Steps to trigger CI/CD when a updated code pushed/merged into specific branch

  

### For ReactJS Front End App

  

Step 1: Login into your server with ssh credentials

  

Step 2: Generate SSH key using command 

\>> ssh-keygen -t ed25519 -C "github-actions-anyname"

  

Step 3: Add the generated key into authorized keys with command

\>> cat ~/.ssh/id\_ed25519.pub >> ~/.ssh/authorized\_keys

  

\>> chmod 600 ~/.ssh/authorized\_keys

  

Also make sure to put the public key into the repository -> settings -> deploy keys (with write permissions enabled) else you will not be able to clone the repository

  

Or

  

Add the ssh key in to account level

  
  

Important: In case you have ssh keys created and added into the deploy keys on repository settings then you need to do the following step to clone the repo on server

1.  nano ~/.ssh/config
    
2.  Put below code
    

Host github-anyname-fe

    HostName github.com

    User git

    IdentityFile ~/.ssh/SSH\_KEY\_FILE\_NAME

    IdentitiesOnly yes

3.  The clone your repo using ssh url but here is the trick you need to add the Host name you have defined in the config then the url become like this
    

  

Actual ssh clone link: [git@github.com](mailto:git@github.com):encalmit-repo/JPSC-ADMIN-FE.git

Modified ssh clone link: git@github-jpsc-admin-fe:encalmit-repo/JPSC-ADMIN-FE.git

  
  
  
  

  

Step 4: Copy the new generated key by cat ~/.ssh/id\_ed25519 and copy the text

\-----BEGIN OPENSSH PRIVATE KEY-----

...

\-----END OPENSSH PRIVATE KEY-----

  
  

Step 5: Go to github account -> Repository for which you are creating CI/CD -> Settings -> Secrets & Variables -> Actions

  

Step 6: Add all these environment variables in Repository secrets

  
  

SSH\_KEY           Value: the newly generated private ssh key on the server

  

SSH\_USER        Value: the user which is used to login into ssh like root@120.323.43.344 (root in this case)

  

SSH\_HOST        Value: domain or ip of the sever

  

APP\_DIR            Value: the location of the app on the server (get inside the folder and use pwd command to get location path)

  

Step 7: Create this file on repository

.github/workflows/deploy-jpsc-fe.yml

  

And put below code in it (change the /.ssh/file path accordingly)

  

name: Deploy JPSC Frontend (Production)

  

on:

  push:

    branches:

      - main

  

jobs:

  deploy:

    runs-on: ubuntu-latest

  

    steps:

      - name: Checkout code

        uses: actions/checkout@v4

  

      - name: Setup SSH

        run: |

          mkdir -p ~/.ssh

          echo "${{ secrets.SSH\_KEY }}" > ~/.ssh/id\_ed25519

          chmod 600 ~/.ssh/id\_ed25519

          ssh-keyscan -H ${{ secrets.SSH\_HOST }} >> ~/.ssh/known\_hosts

  

      - name: Deploy React App via PM2

        run: |

          ssh -o StrictHostKeyChecking=no \\

          ${{ secrets.SSH\_USER }}@${{ secrets.SSH\_HOST }} << 'EOF'

            set -e

  

            echo "➡️ Moving to frontend directory"

            cd ${{ secrets.APP\_DIR }}

  

            echo "🔄 Syncing code with origin/main"

            git fetch origin

            git reset --hard origin/main

            git clean -fd

  

            echo "📦 Installing dependencies (CI-safe)"

            npm ci

  

            echo "🏗️ Building React app"

            npm run build

  

            echo "♻️ Restarting frontend (PM2: JPSC-FE)"

            pm2 restart JPSC-FE || \\

            pm2 start "npm run preview -- --port 5173 --host" \\

              --name JPSC-FE

  

            pm2 save

            echo "✅ Frontend deployment completed successfully"

          EOF