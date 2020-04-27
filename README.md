# CodeStar, Laravel 7.x, MySQL & Redis

This repo is intended to be used on a staging server built with CodeStar. It automaticly deploy your Laravel 7 app to EC2 server configured by CodeStar.

We added some convenient tools and scripts so it reflect most use case.

## This script will (*on top of CodeStar scripts*) :

### Install
 - MySQL
 - Redis

### Configure MySQL
- Root password
- Database name

### Configure your `.env` file without the need to login into the server.
- Your App Name
- *use provided root password*
- *use provided database name*

### Configure your OS
- Timezone

### Run certain command on each deploy
- `php artisan storage:link`
- `php artisan key:generate`
- `php artisan migrate`
- `php artisan db:seed`
> You can add or remove commands to run on each deploy on `scripts/php_artisan` file

## How to use

 1. Go to AWS CodeStar
 2. Click on "PHP (Laravel) Amazon EC2"
 3. Name your project following your conventions
 4. Choose between AWS CodeCommit and GitHub, in both case, choose a repository name that dosn't exist. AWS want to create it from scratch.
 5. Click Next
 6. On the Review project details page, make sure that EC2 configuration are right, that's where you'll choose your instance type, region and VPC (we use the default one for staging servers).
 7. Click Create project
 8. You will be prompted for your EC2 Key pair, choose the one you usually use or create a new one.
 9. Click I acknowledge...
 10. Click Create project
 11. Now let's the system create your repo and install your laravel. The page ask for your tools to help you configure them. Go ahead if you need to, or skip for now.
 12. When the project is successfully created, you'll get on the right side an **Application endpoint**, that's where you'll be able to see your staging app. There's also your **Continuous deployment** status that will help understand understand the health of your deployment.
Go to your source control (CodeCommit or GitHub) clone the repo localy and **Delete everything except the .git folder**.
13. Clone this repository elsewhere then **Copy everything from this repo to your CodeStar one without the .git folder**
14. Configure the `scripts/config` file so it reflect your needs.
15. You are now ready to Commit and Push your changes and enjoy an automated deployment system!

