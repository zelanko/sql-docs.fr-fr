---
title: Non pris en charge les fonctions et les commandes de Visual FoxPro | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- FoxPro ODBC driver [ODBC], commands and functions
- functions [ODBC], Visual FoxPro
- Visual FoxPro ODBC driver [ODBC], commands and functions
- Visual FoxPro commands and functions
- FoxPro ODBC driver
ms.assetid: afdb6b7e-738d-42ca-8053-67ae50873ca6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: db6aff35944b8811e79627c6076ab61e838edf3f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67912320"
---
# <a name="unsupported-visual-foxpro-commands-and-functions-visual-foxpro-odbc-driver"></a>Commandes et fonctions Visual FoxPro non prises en charge (pilote ODBC Visual FoxPro)
Le tableau suivant répertorie les commandes FoxPro et fonctions qui ne sont pas pris en charge par le pilote ODBC Visual FoxPro, mais sont pris en charge par Microsoft® Visual FoxPro.  
  
 Si votre application interagit avec les données dont les règles, les déclencheurs, les valeurs par défaut, ou d’appellent de procédures stockées de ces commandes de Visual FoxPro ou fonctions, le pilote peut générer une erreur.  
  
## <a name="unsupported-visual-foxpro-commands-and-functions"></a>Fonctions et commandes de Visual FoxPro non pris en charge  
  
||||  
|-|-|-|  
|#DEFINE... #UNDEF|#IF... #ENDIF Directive de préprocesseur|#IFDEF &#124; #IFNDEF|  
|#INCLUDE, Directive préprocesseur|:: Opérateur de résolution de portée|! Commande (voir exécution &#124; ! Commande)|  
|? &#124; ?? Command|??? Command|\ &#124; \\\ Commande|  
|@ ... Commande de zone|@ ... Commande de la classe|@ ... Commande Effacer|  
|@ ... MODIFIER - modifier les commandes de zones|@ ... REMPLIR, commande|@ ... GET|  
|@ ... Commande de MENU|@ ... Commande invite|@ ... Par exemple de commande|  
|@ ... Commande de défilement|@ ... À la commande||  
  
## <a name="a"></a>A  
  
||||  
|-|-|-|  
|ACCEPTER la commande|ACLASS (fonction))|Activer la commande de MENU|  
|Activer la commande de menu contextuel|Activer les commandes d’écran|Activer la fenêtre de commande|  
|ActivateCell (méthode)|AJOUTER des commandes de la classe|ADIR (fonction))|  
|AFONT (fonction))|AINSTANCE (fonction))|Variable de mémoire système _ALIGNMENT|  
|AMEMBERS (fonction))|ANSITOOEM (fonction))|APRINTERS (fonction))|  
|ASELOBJ (fonction))|Commande d’assistance||  
  
## <a name="b"></a>b  
  
||||  
|-|-|-|  
|BARRE (fonction))|BARCOUNT (fonction))|BARPROMPT (fonction))|  
|Variable de mémoire système _BEAUTIFY|Variable de mémoire système _BOX|Parcourir les commandes|  
|Variable de mémoire système _BROWSER|Commande de l’application de BUILD|Commande de l’EXE de BUILD|  
|Commande de projet de BUILD|Variable de mémoire système _BUILDER||  
  
## <a name="c"></a>C  
  
||||  
|-|-|-|  
|Variable de mémoire système _CALCVALUE|Variable de mémoire système _CLIPTEXT|Variable de mémoire système _CONVERTER|  
|Variable de mémoire système _CUROBJ|APPELS, commande|Commande d’annulation|  
|CAPSLOCK (fonction))|Commande CD|Commande de changement|  
|Commande CHDIR|CHRSAW (fonction))|Commande de mémo fermer|  
|CNTBAR (fonction))|CNTPAD (fonction))|COL (fonction))|  
|Commande de compilation|COMPILE la commande de base de données|COMPILATION de la commande|  
|COMPOBJ (fonction))|Objet de conteneur|Objet de contrôle|  
|Copiez le fichier, commande|Commande de Mémo de copie|CRÉER des commandes de la classe|  
|CRÉER des commandes CLASSLIB|CRÉER la commande de jeu de couleurs|Commande CREATE|  
|CRÉER la commande de connexion|CRÉER des commandes de base de données|CRÉER des commandes de formulaire|  
|CRÉER à partir de la commande|CRÉER des commandes de l’étiquette|CRÉER la commande de MENU|  
|CRÉER la commande de projet|CRÉER la commande de requête|CRÉER des commandes de rapport|  
|CRÉER des commandes d’écran|CRÉER la commande d’affichage SQL|CRÉER la commande de déclencheur|  
|CRÉER la commande d’affichage|CREATEOBJECT (fonction))|CURDIR (fonction))|  
  
## <a name="d"></a>D  
  
||||  
|-|-|-|  
|Variable de mémoire système _DBLCLICK|Variable de mémoire système _DIARYDATE|DBSETPROP (fonction))|  
|Fonctions DDE|DÉSACTIVER la commande de MENU|DÉSACTIVER la commande de menu contextuel|  
|DÉSACTIVER la fenêtre de commande|DÉCLARER - commande DLL|DÉCLARER la commande|  
|DÉFINIR la barre commande|DÉFINIR la zone commande|DÉFINIR des commandes de la classe|  
|DÉFINIR la commande de MENU|DÉFINIR des commandes de remplissage|DÉFINIR la commande de menu contextuel|  
|DÉFINIR la fenêtre de commande|SUPPRIMER la commande de connexion|SUPPRIMER la commande de base de données|  
|SUPPRIMER le fichier, commande|Commande de déclencheur DELETE|SUPPRIMER la commande d’affichage|  
|Commande DIR|Commande de répertoire|Commande d’affichage|  
|Commande de connexions d’affichage|Commande de base de données d’affichage|Commande de DLL d’affichage|  
|FICHIERS d’affichage (commande)|AFFICHER la mémoire, commande|Commande d’affichage objets|  
|Commande de procédures d’affichage|AFFICHAGE STATUS, commande|Commande STRUCTURE d’affichage|  
|Commande de TABLES d’affichage|Commande de vues d’affichage|NE forment pas commande|  
  
## <a name="e"></a>E  
  
||||  
|-|-|-|  
|MODIFIER la commande|Commande de l’erreur||  
|Effacer (commande)|Commande externe|Commande d’exportation|  
|ÉJECTER commande|ÉJECTER commande PAGE||  
  
## <a name="f"></a>F  
  
||||  
|-|-|-|  
|Variable de mémoire système _FOXDOC|Variable de mémoire système _FOXGRAPH|FEOF (fonction))|  
|FCLOSE (fonction))|FCREATE (fonction))|FGETS (fonction))|  
|FERROR (fonction))|FFLUSH (fonction))|FKLABEL (fonction))|  
|Commande de serveur de fichiers|Rechercher, commande|FOPEN (fonction))|  
|FKMAX (fonction))|FONTMETRIC (fonction))|FSEEK (fonction))|  
|FPUTS (fonction))|FREAD (fonction))||  
|FWRITE (fonction))|FCHSIZE (fonction))||  
  
## <a name="g"></a>G  
  
||||  
|-|-|-|  
|Variable de mémoire système _GENGRAPH|Variable de mémoire système _GENMENU|Variable de mémoire système _GENPD|  
|Variable de mémoire système _GENSCRN|Variable de mémoire système _GENXTAB|GETBAR (fonction))|  
|GETCOLOR (fonction))|GETDIR (fonction))|Commande GETEXPR|  
|GETFILE (fonction))|GETFONT (fonction))|GETOBJECT (fonction))|  
|GETPAD (fonction))|GETPICT (fonction))|GETPRINTER (fonction))|  
  
## <a name="h"></a>H  
  
||||  
|-|-|-|  
|Commande d’aide|Masquer la commande de MENU|Masquer la commande de menu contextuel|  
|Masquer la fenêtre de commande|Accueil () (fonction)||  
  
## <a name="i"></a>I  
  
||||  
|-|-|-|  
|IMESTATUS (fonction))|Commande d’importation|Commandes d’entrée|  
|INDEX de commande|Fonction INKEY)|ISCOLOR (fonction))|  
|Commande INSERT|INSMODE (fonction))||  
|ISMOUSE (fonction))|Variable de mémoire système _INDENT||  
  
## <a name="j"></a>J  
  
||||  
|-|-|-|  
|JOINDRE, commande|||  
  
## <a name="k"></a>K  
  
||||  
|-|-|-|  
|Commande de clavier|||  
  
## <a name="l"></a>L  
  
||||  
|-|-|-|  
|Variable de mémoire système _LMARGIN|Commande de l’étiquette|LASTKEY (fonction))|  
|LINENO (fonction))|LISTES de commandes|Commande de connexions de liste|  
|Commande de chargement|Un fichier LOCFILE (fonction))||  
  
## <a name="m"></a>M  
  
||||  
|-|-|-|  
|MCOL (fonction))|Commande MD|MENU de commande|  
|MÉMOIRE (fonction))|Commande de MENU|Commande MKDIR|  
|MENU (fonction))|MESSAGEBOX (fonction))|MODIFIER la commande de connexion|  
|MODIFIER la commande de la classe|MODIFIER la commande de la commande|MODIFIER la commande|  
|MODIFIER la commande de base de données|MODIFIER le fichier, commande|MODIFIER la commande de mémo|  
|MODIFIER les commandes général|MODIFIER la commande de l’étiquette|MODIFIER la commande de projet|  
|MODIFIER la commande de MENU|Commande de la procédure de modification|Commande de l’écran de modification|  
|MODIFIER la commande de requête|MODIFIER la commande de rapport|MODIFIER la fenêtre de commande|  
|MODIFIER la commande STRUCTURE|MODIFIER la commande d’affichage|DÉPLACER la fenêtre de commande|  
|Commande de la souris|DÉPLACER la commande de menu contextuel|MROW (fonction))|  
|MRKBAR (fonction))|MRKPAD (fonction))||  
|MWINDOW (fonction))|MDOWN (fonction))||  
  
## <a name="n"></a>N  
  
||||  
|-|-|-|  
|Verr. NUM (fonction))|||  
  
## <a name="o"></a>O  
  
||||  
|-|-|-|  
|OBJNUM (fonction))|OBJTOCLIENT (fonction))|Suite à la barre de commande|  
|OEMTOANSI (fonction))|SUR la commande APLABOUT|Commande MENU quitter ON|  
|SUR la commande d’échappement|SUR la barre de commandes de sortie|SUR la clé = commande|  
|Commande de panneau ON EXIT|Commande de menu contextuel ON EXIT|Commande de panneau ON|  
|SUR la commande de l’étiquette de touche|SUR la commande MACHELP|SUR la sélection de barre de commandes|  
|SUR la PAGE de commande|SUR la commande READERROR|SUR la commande de menu contextuel de la sélection|  
|SUR la commande de MENU de sélection|SUR la commande de remplissage de la sélection||  
|SUR la commande d’arrêt|OBJVAR (fonction))||  
  
## <a name="p"></a>P  
  
||||  
|-|-|-|  
|Variable de mémoire système _PADVANCE|Variable de mémoire système _PAGENO|Variable de mémoire système _PBPAGE|  
|Variable de mémoire système _PCOLNO|Variable de mémoire système _PCOPIES|Variable de mémoire système _PDRIVER|  
|Variable de mémoire système _PDSETUP|Variable de mémoire système _PECODE|Variable de mémoire système _PEJECT|  
|Variable de mémoire système _PEPAGE|Variable de mémoire système _PLENGTH|Variable de mémoire système _PLINENO|  
|Variable de mémoire système _PLOFFSET|Variable de mémoire système _PPITCH|Variable de mémoire système _PQUALITY|  
|Variable de mémoire système _PRETEXT|Variable de mémoire système _PSCODE|Variable de mémoire système _PSPACING|  
|Variable de mémoire système _PWAIT|Commande de base de données de PACK|PANNEAU (fonction))|  
|PCOL (fonction))|PEMSTATUS (fonction))|Commande de lecture (macro)|  
|Fenêtre contextuelle de touches|Commande de MENU POP|Commande de menu contextuel POP|  
|Fenêtre contextuelle (fonction))|PRINTJOB... Commande ENDPRINTJOB|PRINTSTATUS (fonction))|  
|PRMBAR (fonction))|PRMPAD (fonction))|Fonction invite)|  
|PROW (fonction))|PRTINFO (fonction))|Commande de clé de PUSH|  
|Commande MENU de PUSH|Commande de menu contextuel de PUSH|PUTFILE (fonction))|  
  
## <a name="q"></a>Q  
  
||||  
|-|-|-|  
|Commande QUIT|||  
  
## <a name="r"></a>R  
  
||||  
|-|-|-|  
|Variable de mémoire système _RMARGIN|Commande de bureau à distance|READKEY (fonction))|  
|Commande de lecture|LIRE la commande de MENU|VERSION de barre de commandes|  
|Fonction Refresh()|Commande de RÉINDEXATION|Commande de bibliothèque de mise en production|  
|Commande CLASSLIB de mise en production|Commande de mise en production|Commande de bloc de mise en production|  
|Commande de MENUS de mise en production|Commande MODULE de mise en production|Commande de WINDOWS mise en production|  
|Commande de fenêtres contextuelles de mise en production|PROCÉDURE de mise en production, commande|La commande Renommer|  
|SUPPRIMER la commande de la classe|RENOMMER une commande de classe|RENOMMER la commande d’affichage|  
|RENOMMER une commande de connexion|RENOMMER une commande de TABLE|RESTAURER à partir de la commande|  
|Commande de rapport|REQUERY (fonction))|RESTAURER la fenêtre de commande|  
|RESTAURER les commandes de MACROS|RESTAURER les commandes d’écran|RGBSCHEME (fonction))|  
|Commande de reprise|RVB (fonction))|EXÉCUTEZ &#124; ! Command|  
|Commande RMDIR|LIGNE (fonction))||  
|Commande RUNSCRIPT|RDLEVEL (fonction))||  
  
## <a name="s"></a>S  
  
||||  
|-|-|-|  
|Enregistrez les MACROS de commandes|ENREGISTRER les commandes d’écran|Enregistrer dans la commande|  
|Enregistrez les commandes WINDOWS|SCHÉMA (fonction))|SCOLS (fonction))|  
|Commande de défilement|Variable de mémoire système _SCREEN|SET, commande|  
|Commande autre SET|SET ANSI, commande|SET APLABOUT, commande|  
|SET, commande enregistrement automatique|SET représentant une cloche, commande|Commande de CLIGNOTEMENT de jeu|  
|Commande de bordure de jeu|Commande BRSTATUS SET|SET CLASSLIB, commande|  
|Commande de suppression de jeu|Commande d’horloge de jeu|DÉFINIR la couleur de la commande|  
|DÉFINIR la couleur de la commande de schéma|JEU de couleurs SET, commande|DÉFINIR la couleur à la commande|  
|SET, commande COMPATIBLE|SET, commande confirmer|Commande de CONSOLE de jeu|  
|ENSEMBLE CPCOMPILE|ENSEMBLE CPDIALOG|Commande de devise SET|  
|CURSEUR de jeu (commande)|Commande de session de données de jeu|Commande de débogage de jeu|  
|SET, commande décimales|Commande de DÉLIMITEURS de jeu|Commande de développement de jeu|  
|Commande de périphérique de jeu|Commande d’affichage de jeu|SET DOHISTORY, commande|  
|SET, commande ECHO|Commande d’échappement de jeu|Commande FORMAT de jeu|  
|SET, commande (fonction)|Commande d’en-têtes SET|Commande HELP SET|  
|SET HELPFILTER, commande|Commande d’intensité SET|Commande SET KEY|  
|SET KEYCOMP, commande|SET LOGERRORS, commande|SET MACDESKTOP, commande|  
|SET MACHELP, commande|SET MACKEY, commande|Commande de marge de jeu|  
|ENSEMBLE marquer de commande|DÉFINIR la marque à la commande|Commande de largeur Mémo SET|  
|Commande MESSAGE SET|Commande de la souris de jeu|Commande de compteur KILOMÉTRIQUE SET|  
|Classes OLEOBJECT SET, commande|Commande PALETTE d’ensemble|SET PDSETUP, commande|  
|Commande de définir le POINT|Commande d’imprimante SET|SET READBORDER, commande|  
|Commande d’actualisation de jeu|Commande de ressources de jeu|Commande de sécurité de jeu|  
|Tableau des scores de SET, commande|SET, commande secondes|Commande de séparateur de jeu|  
|SET, commande ombres|IGNORER de jeu de commande|Commande d’un espace de jeu|  
|SET STATUS, commande|DÉFINIR l’état de barre de commandes|Commande d’étape de jeu|  
|Commande RÉMANENTES SET|SET SYSFORMATS, commande|SET SYSMENU, commande|  
|Commande de discussion d’ensemble|Commande de fusion de texte ensemble|Commande de DÉLIMITEURS ensemble la fusion de texte|  
|Commande de rubrique SET|ID de rubrique SET, commande|SET TRBETWEEN, commande|  
|SET prédictives, commande|Commande de vue d’ensemble|FENÊTRE de l’ensemble de la commande de mémo|  
|SET XCMDFILE, commande|Variable de mémoire système _SHELL|SHOW-GET-Command|  
|SHOW Obtient la commande|Commande de MENU afficher|AFFICHER les commandes de l’objet|  
|AFFICHER la commande de menu contextuel|AFFICHER la fenêtre de commande|Commande de menu contextuel de taille|  
|Taille fenêtre commande|SKPBAR (fonction))|SKPPAD (fonction))|  
|SOUNDEX (fonction))|Variable de mémoire système _SPELLCHK|Fonctions SQL|  
|SROWS (fonction))|Variable de mémoire système _STARTUP|Commande de suspension|  
|Fonctions sys() sauf SYS(2011)|SYSMETRIC (fonction))||  
  
## <a name="t"></a>T  
  
||||  
|-|-|-|  
|Variable de mémoire système _TABS|TEXTE... ENDTEXT commande|TXTWIDTH (fonction))|  
|TRANSFORMER (fonction))|Variable de mémoire système _TRANSPORT||  
|Commande TYPE|Variable de mémoire système _THROTTLE||  
  
## <a name="u"></a>U  
  
||||  
|-|-|-|  
|Fonction de mise à jour)|Utilisez la commande||  
  
## <a name="v"></a>V  
  
||||  
|-|-|-|  
|Commande de base de données de validation|VARREAD (fonction))|VERSION (fonction))|  
  
## <a name="w"></a>W  
  
||||  
|-|-|-|  
|Variable de mémoire système _WINDOWS|Variable de mémoire système _WIZARD|WCHILD (fonction))|  
|ATTENTE de commande|WBORDER (fonction))|WFONT (fonction))|  
|WCOLS (fonction))|WEXIST (fonction))|WLROW (fonction))|  
|AVEC... Commande ENDWITH|WLAST (fonction))|WONTOP (fonction))|  
|W maximum (fonction))|WLCOL (fonction))|WREAD (fonction))|  
|WOUTPUT (fonction))|WMINIMUM (fonction))|WVISIBLE (fonction))|  
|WPARENT (fonction))|WTITLE (fonction))||  
|WROWS (fonction))|Variable de mémoire système _WRAP||  
  
## <a name="z"></a>Z  
  
||||  
|-|-|-|  
|Commande de la fenêtre de ZOOM|||
