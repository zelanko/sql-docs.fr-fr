---
title: Commandes et fonctions Visual FoxPro non prises en charge | Microsoft Docs
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67912320"
---
# <a name="unsupported-visual-foxpro-commands-and-functions-visual-foxpro-odbc-driver"></a>Commandes et fonctions Visual FoxPro non prises en charge (pilote ODBC Visual FoxPro)
Le tableau suivant répertorie les commandes et les fonctions FoxPro qui ne sont pas prises en charge par le pilote ODBC Visual FoxPro, mais qui sont prises en charge par Microsoft® Visual FoxPro®.  
  
 Si votre application interagit avec des données dont les règles, les déclencheurs, les valeurs par défaut ou les procédures stockées appellent ces commandes ou fonctions Visual FoxPro, le pilote peut générer une erreur.  
  
## <a name="unsupported-visual-foxpro-commands-and-functions"></a>Commandes et fonctions Visual FoxPro non prises en charge  
  
||||  
|-|-|-|  
|#DEFINE... #UNDEF|#IF... #ENDIF directive de préprocesseur|#IFDEF &#124; #IFNDEF|  
|Directive de préprocesseur #INCLUDE|:: Scope Resolution, opérateur|! Commande (consultez exécuter &#124; ! Commande|  
|? &#124; ?? Commande|??? Commande|\ &#124; \\\, commande|  
|@ ... BOX, commande|@ ... Commande de classe|@ ... Commande CLEAR|  
|@ ... Commande Modifier/modifier les zones|@ ... FILL, commande|@ ... Télécharger|  
|@ ... Commande de MENU|@ ... Commande PROMPT|@ ... EXEMPLE de commande|  
|@ ... SCROLL, commande|@ ... À la commande||  
  
## <a name="a"></a>Un  
  
||||  
|-|-|-|  
|Commande ACCEPT|ACLASS () (fonction)|Commande de MENU Activer|  
|ACTIVER la commande contextuelle|ACTIVER l’écran, commande|Commande Activer la fenêtre|  
|Méthode ActivateCell|Ajouter une classe, commande|ADIR () (fonction)|  
|AFONT () (fonction)|AINSTANCE () (fonction)|_ALIGNMENT variable de mémoire système|  
|AMEMBERS () (fonction)|ANSITOOEM () (fonction)|APRINTERS () (fonction)|  
|ASELOBJ () (fonction)|Commande ASSIST||  
  
## <a name="b"></a>B  
  
||||  
|-|-|-|  
|Fonction BAR ()|BARCOUNT () (fonction)|BARPROMPT () (fonction)|  
|_BEAUTIFY variable de mémoire système|_BOX variable de mémoire système|Parcourir la commande|  
|_BROWSER variable de mémoire système|CRÉER une application, commande|GÉNÉRER une commande EXE|  
|GÉNÉRER un projet, commande|_BUILDER variable de mémoire système||  
  
## <a name="c"></a>C  
  
||||  
|-|-|-|  
|_CALCVALUE variable de mémoire système|_CLIPTEXT variable de mémoire système|_CONVERTER variable de mémoire système|  
|_CUROBJ variable de mémoire système|Commande CALL|Commande CANCEL|  
|CAPSLOCK () (fonction)|Commande CD|MODIFIER, commande|  
|CHDIR, commande|CHRSAW () (fonction)|FERMER la commande MEMO|  
|CNTBAR () (fonction)|CNTPAD () (fonction)|COL () (fonction)|  
|Compiler (commande)|COMPILER la base de données, commande|COMPILER le formulaire, commande|  
|COMPOBJ () (fonction)|Container (objet)|Objet de contrôle|  
|COPIER le fichier (commande)|COPIER la commande MEMO|Commande CREATe CLASS|  
|CRÉER une commande CLASSLIB|Commande créer un jeu de couleurs|CRÉER une commande|  
|CRÉER une connexion, commande|Commande CREATe DATABASE|CRÉER un formulaire, commande|  
|CRÉER à partir d’une commande|Commande CREATe LABEL|CRÉER une commande de MENU|  
|CRÉER un projet, commande|Commande de création de requête|CRÉER un rapport, commande|  
|CRÉER un écran, commande|CRÉER une commande de vue SQL|Commande CREATe TRIGGER|  
|CRÉER une vue, commande|Fonction CREATEOBJECT ()|Fonction CURDIR ()|  
  
## <a name="d"></a>D  
  
||||  
|-|-|-|  
|_DBLCLICK variable de mémoire système|_DIARYDATE variable de mémoire système|DBSETPROP () (fonction)|  
|Fonctions DDE|DÉSACTIVER la commande de MENU|DÉSACTIVER la commande contextuelle|  
|Commande de désactivation de la fenêtre|Commande DECLARE-DLL|Commande DECLARE|  
|DÉFINIR la barre, commande|DÉFINIR la zone, commande|DÉFINIR la classe, commande|  
|DÉFINIR la commande de MENU|DÉFINIR la commande PAD|DÉFINIR la commande contextuelle|  
|DÉFINIR la fenêtre, commande|SUPPRIMER la connexion, commande|SUPPRIMER la base de données, commande|  
|SUPPRIMER le fichier (commande)|SUPPRIMER le DÉCLENCHEur, commande|SUPPRIMER la vue, commande|  
|DIR, commande|Commande de répertoire|AFFICHER la commande|  
|AFFICHER les connexions, commande|AFFICHER la base de données, commande|AFFICHER les dll, commande|  
|AFFICHER les fichiers, commande|AFFICHER la mémoire, commande|AFFICHER les objets, commande|  
|Commande Afficher les procédures|AFFICHER l’État, commande|AFFICHER la STRUCTURE, commande|  
|Commande Afficher les TABLES|AFFICHER les AFFICHAGEs, commande|Commande DO FORM|  
  
## <a name="e"></a>E  
  
||||  
|-|-|-|  
|MODIFIER, commande|Commande d’erreur||  
|ERASE, commande|Commande externe|Commande d’exportation|  
|Commande EJECT|Commande EJECT PAGE||  
  
## <a name="f"></a>F  
  
||||  
|-|-|-|  
|_FOXDOC variable de mémoire système|_FOXGRAPH variable de mémoire système|FEOF () (fonction)|  
|FCLOSE () (fonction)|FCREATE () (fonction)|FGETS () (fonction)|  
|Fonction de reversion ()|FFLUSH () (fonction)|FKLABEL () (fonction)|  
|Commande de serveur de fichiers|Rechercher, commande|FOPEN () (fonction)|  
|FKMAX () (fonction)|FONTMETRIC () (fonction)|FSEEK () (fonction)|  
|FPUTS () (fonction)|FREAD () (fonction)||  
|FWRITE () (fonction)|FCHSIZE () (fonction)||  
  
## <a name="g"></a>G  
  
||||  
|-|-|-|  
|_GENGRAPH variable de mémoire système|_GENMENU variable de mémoire système|_GENPD variable de mémoire système|  
|_GENSCRN variable de mémoire système|_GENXTAB variable de mémoire système|GETBAR () (fonction)|  
|Fonction GETCOLOR ()|GETDIR () (fonction)|Commande GETEXPR|  
|GETFILE () (fonction)|Fonction GETFONT ()|Fonction GETOBJECT ()|  
|GETPAD () (fonction)|GETPICT () (fonction)|GETPRINTER () (fonction)|  
  
## <a name="h"></a>H  
  
||||  
|-|-|-|  
|AIDE (commande)|MASQUER la commande de MENU|MASQUER la commande contextuelle|  
|MASQUER la fenêtre, commande|Fonction de démarrage ()||  
  
## <a name="i"></a>I  
  
||||  
|-|-|-|  
|Fonction IMESTATUS ()|Commande d’importation|ENTRÉE, commande|  
|INDEX sur la commande|INKEY () (fonction)|ISCOLOR (), fonction|  
|Insérer une commande|INSMODE () (fonction)||  
|ISMOUSE () (fonction)|_INDENT variable de mémoire système||  
  
## <a name="j"></a>J  
  
||||  
|-|-|-|  
|Commande JOIN|||  
  
## <a name="k"></a>K  
  
||||  
|-|-|-|  
|Commande clavier|||  
  
## <a name="l"></a>L  
  
||||  
|-|-|-|  
|_LMARGIN variable de mémoire système|ÉTIQUETTE, commande|LASTKEY () (fonction)|  
|LINENO () (fonction)|Liste des commandes|Liste des connexions, commande|  
|Commande LOAD|LOCFILE () (fonction)||  
  
## <a name="m"></a>M  
  
||||  
|-|-|-|  
|MCOL () (fonction)|Commande MD|MENU à commande|  
|Fonction MEMORY ()|Commande de MENU|MKDIR, commande|  
|Fonction MENU ()|Fonction MESSAGEBOX ()|MODIFIER la connexion, commande|  
|Commande MODIFY CLASS|Commande modifier la commande|Commande modifier le formulaire|  
|Commande modifier la base de données|MODIFIER le fichier (commande)|MODIFIER la commande MEMO|  
|MODIFIER la commande générale|Commande modifier l’étiquette|MODIFIER le projet, commande|  
|MODIFIER la commande de MENU|Commande modifier la procédure|Commande modifier l’écran|  
|MODIFIER la requête, commande|MODIFIER la commande de rapport|Commande modifier la fenêtre|  
|MODIFIER la STRUCTURE, commande|MODIFIER la vue, commande|DÉPLACER la fenêtre, commande|  
|SOURIS, commande|DÉPLACER la commande contextuelle|MROW () (fonction)|  
|MRKBAR () (fonction)|MRKPAD () (fonction)||  
|MWINDOW () (fonction)|MDOWN () (fonction)||  
  
## <a name="n"></a>N  
  
||||  
|-|-|-|  
|Fonction Verr. num ()|||  
  
## <a name="o"></a>O  
  
||||  
|-|-|-|  
|OBJNUM () (fonction)|OBJTOCLIENT () (fonction)|Commande sur la barre|  
|OEMTOANSI () (fonction)|SUR la commande APLABOUT|EN QUITTant la commande de MENU|  
|Commande ON ESCAPE|Dans la barre de sortie, commande|ON KEY =, commande|  
|À la fin de la commande PAD|Commande contextuelle à la sortie|Commande ON PAD|  
|Commande sur une étiquette de clé|SUR la commande MACHELP|Dans la barre de sélection, commande|  
|SUR la PAGE, commande|SUR la commande READERROR|Commande contextuelle à la sélection|  
|Dans la commande de MENU de sélection|Dans la commande de bloc de sélection||  
|À la commande SHUTDOWN|OBJVAR () (fonction)||  
  
## <a name="p"></a>P  
  
||||  
|-|-|-|  
|_PADVANCE variable de mémoire système|_PAGENO variable de mémoire système|_PBPAGE variable de mémoire système|  
|_PCOLNO variable de mémoire système|_PCOPIES variable de mémoire système|_PDRIVER variable de mémoire système|  
|_PDSETUP variable de mémoire système|_PECODE variable de mémoire système|_PEJECT variable de mémoire système|  
|_PEPAGE variable de mémoire système|_PLENGTH variable de mémoire système|_PLINENO variable de mémoire système|  
|_PLOFFSET variable de mémoire système|_PPITCH variable de mémoire système|_PQUALITY variable de mémoire système|  
|_PRETEXT variable de mémoire système|_PSCODE variable de mémoire système|_PSPACING variable de mémoire système|  
|_PWAIT variable de mémoire système|Commande PACK DATABASE|Fonction PAD ()|  
|PCOL () (fonction)|PEMSTATUS () (fonction)|LIRE la MACRO, commande|  
|Commande POP KEY|MENU contextuel, commande|Fenêtre contextuelle contextuelle|  
|Fonction POPUP ()|PRINTJOB... Commande ENDPRINTJOB|PRINTSTATUS () (fonction)|  
|PRMBAR () (fonction)|PRMPAD () (fonction)|Fonction PROMPT ()|  
|PROW () (fonction)|PRTINFO () (fonction)|Commande PUSH KEY|  
|Commande de MENU PUSH|Commande PUSH contextuelle|PUTFILE () (fonction)|  
  
## <a name="q"></a>Q  
  
||||  
|-|-|-|  
|Commande QUIT|||  
  
## <a name="r"></a>R  
  
||||  
|-|-|-|  
|_RMARGIN variable de mémoire système|RD, commande|READKEY () (fonction)|  
|LIRE, commande|LIRE la commande de MENU|Commande de la barre de lancement|  
|Fonction REFRESH ()|Commande de réindexation|Commande de la bibliothèque de mise en version|  
|Commande RELEASE CLASSLIB|Commande RELEASE|Commande RELEASE PAD|  
|Commande MENUS RELEASE|Commande du MODULE de version|Commande WINDOWS RELEASE|  
|Commande contextuels de mise en version|Commande de procédure de lancement|Renommer, commande|  
|Commande REMOVE CLASS|Renommer la classe, commande|Renommer la vue, commande|  
|Renommer la commande de connexion|Renommer la TABLE, commande|RESTAURER à partir de la commande|  
|Commande de rapport|Fonction Requery ()|Commande restaurer la fenêtre|  
|Commande Restore MACROs|Commande restaurer l’écran|RGBSCHEME () (fonction)|  
|RESUME, commande|Fonction RGB ()|EXÉCUTEZ &#124; ! Commande|  
|RMDIR, commande|Fonction ROW ()||  
|Commande RUNSCRIPT|RDLEVEL () (fonction)||  
  
## <a name="s"></a>S  
  
||||  
|-|-|-|  
|Commande Enregistrer les MACROs|ENREGISTRER l’écran, commande|ENREGISTRER dans la commande|  
|ENREGISTRER la commande WINDOWS|Fonction SCHEMe ()|SCOLS () (fonction)|  
|SCROLL, commande|_SCREEN variable de mémoire système|Commande SET|  
|DÉFINIR une autre commande|SET ANSI, commande|DÉFINIR la commande APLABOUT|  
|SET autosave, commande|DÉFINIR la commande BELL|DÉFINIR la commande BLINK|  
|DÉFINIR la bordure, commande|DÉFINIR la commande BRSTATUS|DÉFINIR la commande CLASSLIB|  
|DÉFINIR la commande CLEAR|SET CLOCK (commande)|DÉFINIR la couleur de la commande|  
|DÉFINIR la couleur de la commande de schéma|Commande SET COLOR SET|DÉFINIR la couleur sur la commande|  
|DÉFINIR la commande COMPATIBLE|DÉFINIR la commande CONFIRM|DÉFINIR une commande de CONSOLE|  
|DÉFINIR CPCOMPILE|DÉFINIR CPDIALOG|SET CURRENCY, commande|  
|SET CURSOR, commande|DÉFINIR la commande DATASESSION|DÉFINIR la commande de débogage|  
|SET DECIMALs, commande|Commande SET Delimiters|DÉFINIR la commande de développement|  
|SET DEVICE, commande|DÉFINIR la commande d’affichage|DÉFINIR la commande de l’historique|  
|DÉFINIR la commande ECHO|SET ESCAPE, commande|DÉFINIR le FORMAT, commande|  
|Commande SET FUNCTION|DÉFINIR les en-têtes, commande|DÉFINIR l’aide, commande|  
|DÉFINIR la commande HELPFILTER|DÉFINIR la commande INTENSity|DÉFINIR la clé, commande|  
|DÉFINIR la commande keycomp|DÉFINIR la commande LOGERRORS|DÉFINIR la commande MACDESKTOP|  
|DÉFINIR la commande MACHELP|DÉFINIR la commande MACKEY|SET MARGIN, commande|  
|DÉFINIR la marque de la commande|DÉFINIR la commande Marquer pour|DÉFINIR la commande MEMOWIDTH|  
|DÉFINIR le MESSAGE, commande|DÉFINIR la souris, commande|SET kilométrique, commande|  
|SET OLEOBJECT, commande|DÉFINIR la PALETTE, commande|DÉFINIR la commande PDSETUP|  
|Commande SET POINT|Commande SET PRINTER|DÉFINIR la commande READBORDER|  
|DÉFINIR la commande ACTUALISer|SET Resource, commande|Commande SET SAFETY|  
|SET SCOREBOARD, commande|Commande SET SECONDS|Commande SET SEPARATOR|  
|DÉFINIR SHADOWs, commande|DÉFINIR ignorer la commande|SET SPACE, commande|  
|SET STATUs (commande)|DÉFINIR la barre d’État, commande|Commande SET STEP|  
|DÉFINIR la commande RÉMANENTe|DÉFINIR la commande SYSFORMATS|DÉFINIR la commande SYSMENU|  
|DÉFINIR la commande parler|DÉFINIR la commande TEXTMERGE|Commande SET TEXTMERGE Delimiters|  
|Commande SET TOPIC|Commande SET TOPIC ID|DÉFINIR la commande TRBETWEEN|  
|DÉFINIR la commande TYPEAHEAD|SET VIEW, commande|SET WINDOW OF MEMO, commande|  
|DÉFINIR la commande XCMDFILE|_SHELL variable de mémoire système|AFFICHER la commande d’extraction|  
|Commande SHOW obtient|AFFICHER la commande de MENU|Commande SHOW OBJECT|  
|AFFICHER la commande contextuelle|AFFICHER la fenêtre, commande|Fenêtre contextuelle de la taille|  
|FENÊTRE taille, commande|SKPBAR () (fonction)|SKPPAD () (fonction)|  
|Fonction SOUNDEX ()|_SPELLCHK variable de mémoire système|Fonctions SQL|  
|SROWS () (fonction)|_STARTUP variable de mémoire système|Commande SUSPEND|  
|Fonctions SYS (), à l’exception de SYS (2011)|SYSMETRIC () (fonction)||  
  
## <a name="t"></a>T  
  
||||  
|-|-|-|  
|_TABS variable de mémoire système|TEXTE... Commande ENDTEXT|Fonction TXTWIDTH ()|  
|Fonction TRANSFORM ()|_TRANSPORT variable de mémoire système||  
|Commande de TYPE|_THROTTLE variable de mémoire système||  
  
## <a name="u"></a>U  
  
||||  
|-|-|-|  
|Fonction UPDATEd ()|UTILISER la commande||  
  
## <a name="v"></a>V  
  
||||  
|-|-|-|  
|Commande valider la base de données|VARREAD () (fonction)|VERSION () (fonction)|  
  
## <a name="w"></a>W  
  
||||  
|-|-|-|  
|_WINDOWS variable de mémoire système|_WIZARD variable de mémoire système|WCHILD () (fonction)|  
|WAIT, commande|WBORDER () (fonction)|WFONT () (fonction)|  
|WCOLS () (fonction)|WEXIST () (fonction)|WLROW () (fonction)|  
|AVEC... Commande ENDWITH|WLAST () (fonction)|WONTOP () (fonction)|  
|WMAXIMUM () (fonction)|WLCOL () (fonction)|WREAD () (fonction)|  
|WOUTPUT () (fonction)|WMINIMUM () (fonction)|WVISIBLE () (fonction)|  
|WPARENT () (fonction)|WTITLE () (fonction)||  
|WROWS () (fonction)|_WRAP variable de mémoire système||  
  
## <a name="z"></a>Z  
  
||||  
|-|-|-|  
|FENÊTRE ZOOM, commande|||
