# git-bash-setup

Git Bash skulle gerne være installeret på forhånd fra vi installerede Git. Hvis ikke så kør [Git installer'en](https://git-scm.com/downloads).

Når du åbner Git Bash skulle du gerne se noget lignende dette  
![](ugly_git_bash.png)

Personlig er jeg ikke fan af den *prompt*, så lad os customize den lidt.

Vi starter med at åbne Git Bash og skrive
```
$ cd ~
```
Dette vil sikre os vi er i vores *home directory*

Derefter vil vi oprette en ny fil kaldet **.bash_profile**
```
$ touch .bash_profile
```
Referer til **#terminal-commands** på discord hvis du er usikker på hvad de følgende kommandoer gør.

...how to vim

Indsæt derefter følgende i den nyoprettede **.bash_profile**
```bash
# Her sætter vi vores farver, dette er bare lokale variabler
username_color=$(tput setaf 7);
directory_color=$(tput setaf 3);
general_text_color=$(tput setaf 7);
start_color=$(tput setaf 1);
branch_color=$start_color; # Samme farve som start_color - $(tput setaf 1)
bold=$(tput bold);
reset=$(tput sgr0);

# Her ændre vi vores prompt
PS1="\[${bold}\]";
PS1+="\[${username_color}\]\u";
PS1+="\[${general_text_color}\] in ";
PS1+="\[${directory_color}\]\W ";
PS1+="\[${branch_color}\]\$(__git_ps1 '(%s) ')"
PS1+="\[${start_color}\]\$ \[${reset}\]";

export PS1 # Når vi er færdige eksportere vi variablet
```