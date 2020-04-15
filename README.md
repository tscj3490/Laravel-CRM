# What is Laravel CRM?
<p>This project is a remake of my barebones Client Management System using Laravel 5.5. You can view the original <a href="https://github.com/kkamara/crm">here</a>.</p>

# Installation
<p>Ensure you have <a href="http://php.net/downloads.php">php 7.0+</a> and <a href='https://getcomposer.org/'>Composer</a> installed <a href="https://laravel.com/docs/5.5/database#configuration">database engine</a> of your choosing, preferably Mariadb or MySQL.</p>
<p>Also make sure you have the latest version of <a href="https://nodejs.org/en/">NodeJS</a> and <a href="https://www.npmjs.com/">NPM</a> installed.</p>
<p>1. Open the command line and run:</p>
<p><pre>git clone https://github.com/kkamara/laravel-crm [installation-path]</pre></p>
<p>
  <span>2. Rename the file <b>.env.example</b> to <b>.env</b> and then update the contents with your database connection.</span>
  <br>
  <span><a href='https://laravel.com/docs/5.5/configuration#environment-configuration'>Click here for further assistance</a></span>
 </p>
<p>3. Go to the folder you downloaded Laravel CRM to and run the following in the command line:</p>
<p>To update project dependencies where necessary:</p>
<p><pre>npm update;composer update</pre></p>
<p>To generate a secure hash for the project:</p>
<p><pre>php artisan key:generate</pre></p>
<p>To link the public folder and storage folder:</p>
<p><pre>php artisan storage:link</pre></p>
<p>4. Run the following to establish the required data schema in your chosen database:</p>
<p><pre>php artisan migrate</pre></p>
<p>5. Now we will generate fake data:</p>
<p>Open Laravel Tinker by running:</p>
<p><pre>php artisan tinker</pre></p>
<p>And run the following</p>
<p><pre>
  /*
   * Using database/factories/UserFactory.php we will generate
   * fake records for logs, clients and users
   */
  factory('App\Log', 200)->create(); // Change 200 to your desired number
</pre></p>
<p>Then close Tinker with <code>exit</code> or <code>CTRL-Z</code>.</p>
<p>6. Setting up roles and permissions</p>
<p>Run the following in the installation folder:</p>
<p><pre>php artisan db:seed --class=PermissionsTableSeeder</pre></p>
<p><pre>php artisan db:seed --class=RolesTableSeeder</pre></p>
<p>7. Run the following to start your local server:</p>
<p><pre>php artisan serve</pre></p>
<p>You should now be able to access the project by entering <code>http://localhost:8000</code> into your web browser.</p>

# Granting Access Privileges
<p>After completing the steps in the Installation section you should have Laravel CRM ready to run on your local system with fake data contained in a database of your choosing. If so, you can take the following steps to assign roles to users in order to grant access to project features.</p>
<p>Open a terminal shell in the project directory and enter the following command</p>
<p><pre>php artisan tinker</pre></p>
<p>Within Tinker you can now find a user and assign roles and permissions with the following example.</p>
<p><pre>// Get user of your choosing
$u = App\User::find(1);
</pre></p>
<p><pre>/*
/* associate the user with a defined role (recommended)
/* each role grants permissions related to the access level you would expect by the role name
 */
$u->assignRole('admin'); // roles: 'admin', 'client_admin', 'client_user'
</pre></p>
<p><pre>
// assign permissions to the user
$u->givePermissionTo($string); // replace $string with the name of the permission stored in the database
</pre></p>
<p>To be able to view a particular client you will have to access your database and insert a user_id and client_id row within the client_user table and ensure your user has the necessary access privileges.</p>

# Popular APIs Included
<ul>
<li><a href="https://github.com/spatie/laravel-permission">Spatie's laravel-permissions</a></li>
  <li><a href="https://developers.google.com/gmail/api/guides/">Gmail API</a></li>
</ul>

<p>Front end design by <a href="https://codepen.io/j_holtslander/pen/XmpMEp">maridlcrmn & j_holtslander</a>.</p>
