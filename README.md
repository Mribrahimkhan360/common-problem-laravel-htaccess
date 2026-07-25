# common-problem-laravel-htaccess

Step 1: Create a .htaccess File in the Root (public_html)
Create a .htaccess file inside the root of your project ( public_html/.htaccess) with the following contents:

<IfModule mod_rewrite.c>
    RewriteEngine On

    # Redirect all requests to public/index.php
    RewriteCond %{REQUEST_URI} !^/public/
    RewriteRule ^(.*)$ public/$1 [L,QSA]
</IfModule>
What this does:
It silently redirects every request to Laravel public folder, where index.php lives without exposing that in the URL.

Step 2: Verify Laravel Default .htaccess Inside public
Make sure the default Laravel .htaccess file exists inside the public folder. It usually comes with Laravel by default, but check to be safe:

<IfModule mod_rewrite.c>
    <IfModule mod_negotiation.c>
        Options -MultiViews -Indexes
    </IfModule>

    RewriteEngine On

    # Handle Authorization Header
    RewriteCond %{HTTP:Authorization} .
    RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]

    # Redirect all other requests to index.php
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteRule ^ index.php [L]
</IfModule>
Then upload the full vendor folder and update your .env file.
