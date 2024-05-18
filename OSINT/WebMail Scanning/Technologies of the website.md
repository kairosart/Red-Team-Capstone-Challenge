Using a plugin for the browser called Wappalyzer, we can check on the technologies used by the server, including their versions (if available):


![[techwebmail.png]]

As we can see, the server is not only using RoundCube, but it is also using PHP. Looking into the GitHub repository, it is possible to identify that there is a main index.php page, which redirects us to the default login application page, which might give us another target for a brute force attack.

![[roundcube.png]]

