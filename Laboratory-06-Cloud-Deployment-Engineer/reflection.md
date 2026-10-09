# Mission Reflection

**1. Compose vs. manual commands.** Before this lab I would have needed several long commands to start Nextcloud and a database, and I would have had to link them myself. With a docker-compose.yml, everything is written down once and started with one command. If I make a mistake, I just fix a line in the file and run it again, which is much faster than retyping. The file can also be saved on GitHub and shared with anyone.

**2. Indentation errors.** YAML uses spaces to show structure, so a Tab or a wrong number of spaces confuses it. Docker Compose will refuse to run and print an error such as "mapping values are not allowed" or "found character that cannot start any token." Nothing gets deployed until the spacing is fixed. That is why I double-checked my file with the cat command.

**3. Environment variables.** The variables like MYSQL_PASSWORD let me give the containers their settings without changing the images. Both containers need to share the same database name, user, and password so they can connect. It also keeps the settings in one easy place. In a real company, secrets like passwords should be stored in a separate protected file, not written directly in the code.

**4. How it felt.** Honestly, it felt surprising. I typed a short file, ran one command, and a few minutes later a real private cloud system was open in my browser. Something that sounds very advanced turned out to be approachable, and that boosted my confidence.

**5. My understanding since Mission 1.** In Mission 1, I saw cloud computing as simply "using someone else's computers." Now I see it as a way of building and running systems through code, automation, and containers. I am starting to understand why engineers say to write infrastructure instead of clicking through it.
