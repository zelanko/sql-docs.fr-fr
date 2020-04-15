---
title: Commandes et fonctions Visual FoxPro non étayées (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7e5b8ed06ad9f996d644df0dfb99d15adcff86bc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307650"
---
# <a name="unsupported-visual-foxpro-commands-and-functions-visual-foxpro-odbc-driver"></a>Commandes et fonctions Visual FoxPro non prises en charge (pilote ODBC Visual FoxPro)
Le tableau suivant répertorie les commandes et les fonctions FoxPro qui ne sont pas prises en charge par le visual FoxPro ODBC Driver, mais qui sont prises en charge par Microsoft® Visual FoxPro®.  
  
 Si votre application interagit avec les données dont les règles, les déclencheurs, les valeurs par défaut ou les procédures stockées appellent ces commandes ou fonctions Visual FoxPro, le pilote peut générer une erreur.  
  
## <a name="unsupported-visual-foxpro-commands-and-functions"></a>Commandes et fonctions Visuelles FoxPro non étayées  
  
||||  
|-|-|-|  
|#DEFINE ... #UNDEF|#IF ... directive préprocesseur #ENDIF|#IFDEF #IFNDEF &#124;|  
|directive #INCLUDE préprocesseur|:: Opérateur de résolution de portée|! Commande (voir RUN &#124; ! Commande)|  
|? &#124; ?? Commande|??? Commande|&#124; \\'Commande'|  
|@ ... Commande BOX|@ ... Commande CLASS|@ ... Commande CLEAR|  
|@ ... EDIT - Modifier les boîtes de commande|@ ... Commandement FILL|@ ... Avoir|  
|@ ... Commande MENU|@ ... Commandement PROMPT|@ ... Commande SAY|  
|@ ... Commande SCROLL|@ ... À Commander||  
  
## <a name="a"></a>Un  
  
||||  
|-|-|-|  
|Commandement ACCEPT|ACLASS) ) Fonction|Commande ACTIVE MENU|  
|Commande POPUP ACTIVE|Commande SCREEN ACTIVATE|Commande DE WINDOW ACTIVE|  
|Méthode ActivateCell|Commande ADD CLASS|ADIR( ) Fonction|  
|AFONT( ) Fonction|AINSTANCE( ) Fonction|_ALIGNMENT variable de mémoire du système|  
|AMEMBERS( ) Fonction|ANSITOOEM( ) Fonction|APRINTERS( ) Fonction|  
|ASELOBJ( ) Fonction|Commandement ASSIST||  
  
## <a name="b"></a>B  
  
||||  
|-|-|-|  
|BAR( ) Fonction|BARCOUNT( ) Fonction|BARPROMPT( ) Fonction|  
|_BEAUTIFY Variable de Mémoire du système|_BOX Variable de mémoire du système|Commande BROWSE|  
|_BROWSER Variable de mémoire du système|Commande BUILD APP|Build EXE Commande|  
|Commande BUILD PROJECT|_BUILDER Variable de mémoire du système||  
  
## <a name="c"></a>C  
  
||||  
|-|-|-|  
|_CALCVALUE variable de mémoire du système|_CLIPTEXT Variable de mémoire du système|_CONVERTER variable de mémoire du système|  
|_CUROBJ Variable de mémoire du système|Commande CALL|Commande CANCEL|  
|CAPSLOCK( ) Fonction|Commande DE CD|Commande CHANGE|  
|Commandement CHDIR|CHRSAW( ) Fonction|Commandement CLOSE MEMO|  
|CNTBAR( ) Fonction|CNTPAD) ) Fonction|COL( ) Fonction|  
|Commande COMPILE|Commande COMPILE DATABASE|Commande COMPILE FORM|  
|COMPOBJ( ) Fonction|Objet de conteneur|Objet de contrôle|  
|Commande COPY FILE|Commande COPY MEMO|Commande CREATE CLASS|  
|CREATE CLASSLIB Commande|CREATE COLOR SET Commande|Commande CREATE|  
|Commande CREATE CONNECTION|Commande CREATE DATABASE|Commande FORM CREATE|  
|CREATE DE Commande|Commande CREATE LABEL|Commande CREATE MENU|  
|Commande DE PROJET CREATE|Commandement DE LA REQUÊTE CREATE|Commande DE RAPPORT CREATE|  
|Commande SCREEN CREATE|CREATE SQL VIEW Commande|COMMANDE CREATE TRIGGER|  
|Commande CREATE VIEW|CREATEOBJECT( ) Fonction|CURDIR( ) Fonction|  
  
## <a name="d"></a>D  
  
||||  
|-|-|-|  
|_DBLCLICK Variable de mémoire du système|_DIARYDATE Variable de mémoire du système|DBSETPROP( ) Fonction|  
|Fonctions DDE|COMMANDE DEACTIVATE MENU|DEACTIVATE POPUP Command|  
|Commande WINDOW DEACTIVATE|DECLARE - Commandement DLL|Commande DE POSTE|  
|Commande DE LA BAR DEFINE|Commande DE LA BOX DEFINE|Commande DE LA CLASSE DE DEFINE|  
|COMMANDE DE DEFINE MENU|Commande PAD DEFINE|DÉCRIVEZ POPUP Command (en)|  
|Commande DE LA FENÊTRE DE DEFINE|Commande DELETE CONNECTION|Commande DATABASE DELETE|  
|Commande DE FILE DELETE|Commande TRIGGER DELETE|Commande DE VUE SUPPRIMER|  
|Commandement DIR|Commande DIRECTORY|Commande DISPLAY|  
|Display CONNECTIONS Commande|Display DATABASE Commande|DISPLAY DLLS Commande|  
|Display FILES Commande|Display MEMORY Commande|Display OBJECTS Commande|  
|DISPLAY PROCEDURES Commande|Display STATUS Commande|Commande DISPLAY STRUCTURE|  
|Display TABLES Commande|Display VIEWS Commande|Commande DO FORM|  
  
## <a name="e"></a>E  
  
||||  
|-|-|-|  
|Commande EDIT|Commande ERROR||  
|Commande ERASE|Commandement EXTERNAL|Commandement EXPORT|  
|Commandement EJECT|Commandement EJECT PAGE||  
  
## <a name="f"></a>F  
  
||||  
|-|-|-|  
|_FOXDOC Variable de mémoire du système|_FOXGRAPH Variable de mémoire du système|FEOF( ) Fonction|  
|FCLOSE( ) Fonction|FCREATE( ) Fonction|FGETS( ) Fonction|  
|FERROR( ) Fonction|FFLUSH) ) Fonction|FKLABEL( ) Fonction|  
|Commandement FILER|Commande FIND|FOPEN( ) Fonction|  
|FKMAX) ) Fonction|FONTMETRIC( ) Fonction|FSEEK( ) Fonction|  
|FPUTS( ) Fonction|FREAD( ) Fonction||  
|FWRITE( ) Fonction|FCHSIZE( ) Fonction||  
  
## <a name="g"></a>G  
  
||||  
|-|-|-|  
|_GENGRAPH Variable de mémoire du système|_GENMENU Variable de mémoire du système|_GENPD Variable de mémoire du système|  
|_GENSCRN Variable de mémoire du système|_GENXTAB variable de mémoire du système|GETBAR( ) Fonction|  
|GETCOLOR( ) Fonction|GETDIR( ) Fonction|Commandement GETEXPR|  
|GETFILE( ) Fonction|GETFONT( ) Fonction|GETOBJECT( ) Fonction|  
|GETPAD) ) Fonction|GETPICT( ) Fonction|GETPRINTER( ) Fonction|  
  
## <a name="h"></a>H  
  
||||  
|-|-|-|  
|Commande HELP|Hide MENU Commande|Hide POPUP Commande|  
|Commande DE WINDOW HIDE|HOME) ) Fonction||  
  
## <a name="i"></a>I  
  
||||  
|-|-|-|  
|IMESTATUS( ) Fonction|Commandement IMPORT|Commande INPUT|  
|INDEX ON Commande|INKEY) ) Fonction|ISCOLOR) ) Fonction|  
|Commande INSERT|INSMODE( ) Fonction||  
|ISMOUSE( ) Fonction|_INDENT variable de mémoire du système||  
  
## <a name="j"></a>J  
  
||||  
|-|-|-|  
|Commande JOIN|||  
  
## <a name="k"></a>K  
  
||||  
|-|-|-|  
|Commande KEYBOARD|||  
  
## <a name="l"></a>L  
  
||||  
|-|-|-|  
|_LMARGIN variable de mémoire du système|Commande LABEL|LASTKEY( ) Fonction|  
|LINENO( ) Fonction|Commandes LIST|Commande LIST CONNECTIONS|  
|LOAD Command|LOCFILE( ) Fonction||  
  
## <a name="m"></a>M  
  
||||  
|-|-|-|  
|MCOL( ) Fonction|Commandement MD|MENU TO Commande|  
|MEMORY( ) Fonction|Commande MENU|Commandement MKDIR|  
|MENU( ) Fonction|MESSAGEBOX( ) Fonction|Commande DE CONNECTION DE MODI|  
|Commande DE CLASSE DE MODI|Commande COMMAND DE MODI|Commande FORM DE MODI|  
|Commande DE DATABASE DE MODI|Commande MODI FILE|Commande DE MEMO DE MODI|  
|Commande GENERAL DE MODIFICATION|Commande DE LABEL DE MODI|Commande DE PROJECT DE MODIFICATION|  
|Commande DE MENU DE MODIFICATION|Commande DE PROCÉDURE DE MODIFICATION|Commande SCREEN MODI|  
|Commande DE QUESTIONRY DE MODIFICATION|Commande RAPPORT MODI|Commande DE WINDOW DE MODI|  
|Commande STRUCTURE DE MODIFICATION|Commande DE VUE DE MODI|Commande MOVE WINDOW|  
|Commande MOUSE|Move POPUP Commande|MROW) ) Fonction|  
|FONCTION MRKBAR( )|MRKPAD) ) Fonction||  
|MWINDOW( ) Fonction|MDOWN) ) Fonction||  
  
## <a name="n"></a>N  
  
||||  
|-|-|-|  
|NUMLOCK( ) Fonction|||  
  
## <a name="o"></a>O  
  
||||  
|-|-|-|  
|OBJNUM) ) Fonction|OBJTOCLIENT( ) Fonction|Commandement ON BAR|  
|OEMTOANSI( ) Fonction|SUR APLABOUT Command|ON EXIT MENU Command|  
|Sur ESCAPE Command|ON EXIT BAR Command|SUR KEY - Commande|  
|SUR EXIT PAD Command|SUR EXIT POPUP Command|Sur le commandement DE PAD|  
|Sur KEY LABEL Command|Sur LE COMMANDEMENT MACHELP|ON SELECTION BAR Command|  
|Sur PAGE Command|Sur READERROR Commande|SUR SELECTION POPUP Command|  
|ON SELECTION MENU Commande|SUR SELECTION PAD Command||  
|Sur LE COMMANDEMENT SHUTDOWN|OBJVAR( ) Fonction||  
  
## <a name="p"></a>P  
  
||||  
|-|-|-|  
|_PADVANCE Variable de Mémoire du système|_PAGENO Variable de mémoire du système|_PBPAGE Variable de mémoire du système|  
|_PCOLNO Variable de mémoire du système|_PCOPIES variable de mémoire du système|_PDRIVER variable de mémoire du système|  
|_PDSETUP Variable de mémoire du système|_PECODE Variable de mémoire du système|_PEJECT variable de mémoire du système|  
|_PEPAGE variable de mémoire du système|_PLENGTH Variable de mémoire du système|_PLINENO Variable de mémoire du système|  
|_PLOFFSET Variable de mémoire du système|_PPITCH Variable de mémoire du système|_PQUALITY Variable de mémoire du système|  
|_PRETEXT Variable de mémoire du système|_PSCODE Variable de mémoire du système|_PSPACING Variable de mémoire du système|  
|_PWAIT Variable de mémoire du système|Pack DATABASE Commande|PAD( ) Fonction|  
|PCOL( ) Fonction|PEMSTATUS( ) Fonction|PLAY MACRO Commande|  
|Commandement POP KEY|Commande POP MENU|Commandement POPUP POPUP|  
|POPUP( ) Fonction|PRINTJOB ... Commande ENDPRINTJOB|PRINTSTATUS( ) Fonction|  
|PRMBAR( ) Fonction|PRMPAD) ) Fonction|PROMPT( ) Fonction|  
|PROW( ) Fonction|PRTINFO( ) Fonction|Commande PUSH KEY|  
|Commande PUSH MENU|Commande PUSH POPUP|FONCTION PUTFILE( )|  
  
## <a name="q"></a>Q  
  
||||  
|-|-|-|  
|Commande QUIT|||  
  
## <a name="r"></a>R  
  
||||  
|-|-|-|  
|_RMARGIN Variable de mémoire du système|Commandement DE la RD|READKEY( ) Fonction|  
|LIRE Commande|LIRE AUSSI - Commande|RELEASE BAR Command|  
|FONCTION REFRESH()|Commande REINDEX|RELEASE LIBRARY Command|  
|RELEASE CLASSLIB Commande|Commande RELEASE|RELEASE PAD Command|  
|Release MENUS Commande|Release MODULE Commande|Release WINDOWS Commande|  
|Release POPUPS Commande|Release PROCEDURE Commande|Commande RENAME|  
|REMOVE CLASS Command|RENAME CLASS Command|ReNAME VIEW Commande|  
|ReNAME CONNECTION Commande|RENAME TABLE Command|RESTORE FROM Command|  
|Commande REPORT|REQUERY( ) Fonction|Commande WINDOW RESTORE|  
|COMMANDE MACROS RESTAUR|COMMANDE SCREEN RESTORE|RGBSCHEME( ) Fonction|  
|Commande RESUME|RGB) ) Fonction|RUN &#124; ! Commande|  
|Commandement RMDIR|ROW( ) Fonction||  
|Commande RUNSCRIPT|RDLEVEL( ) Fonction||  
  
## <a name="s"></a>S  
  
||||  
|-|-|-|  
|SAVE MACROS Commande|Commande SCREEN SAVE|SAVE TO Command|  
|Commande WINDOWS SAVE|SCHEME( ) Fonction|SCOLS( ) Fonction|  
|Commande SCROLL|_SCREEN Variable de mémoire du système|Commande SET|  
|SET ALTERNATE Commande|SET ANSI, commande|Set APLABOUT Commande|  
|SET AUTOSAVE Commande|Set BELL Commande|Set BLINK Commande|  
|Set BORDER Commande|Set BRSTATUS Commande|Set CLASSLIB Commande|  
|Set CLEAR Commande|Set CLOCK Commande|SET COLOR OF Commande|  
|SET COLOR OF SCHEME Command|SET COLOR SET Commande|SET COLOR À Commande|  
|Set COMPATIBLE Commande|Set CONFIRM Commande|Commande SET CONSOLE|  
|DÉFINIR CPCOMPILE|DÉFINIR CPDIALOG|Set CURRENCY Commande|  
|Set CURSOR Commande|SET DATASESSION Commande|Set DEBUG Commande|  
|SET DECIMALS Commande|SET DELIMITERS Commande|Set DEVELOPMENT Commande|  
|Commande SET DEVICE|Set DISPLAY Commande|SET DOHISTORY Commande|  
|Set ECHO Commande|Set ESCAPE Commande|Commande SET FORMAT|  
|Set FUNCTION Commande|Set HEADINGS Commande|Set HELP Commande|  
|Set HELPFILTER Commande|Set INTENSITY Commande|Set KEY Commande|  
|Set KEYCOMP Commande|Set LOGERRORS Commande|SET MACDESKTOP Commande|  
|Set MACHELP Commande|Set MACKEY Commande|Set MARGIN Commande|  
|SET MARK OF Commande|SET MARK À Commande|SET MEMOWIDTH Commande|  
|Set MESSAGE Commande|Commande SET MOUSE|Set ODOMETER Commande|  
|SET OLEOBJECT Commande|Commande SET PALETTE|SET PDSETUP Commande|  
|Set POINT Commande|Commande SET PRINTER|SET READBORDER Commande|  
|SET REFRESH Commande|Set RESOURCE Commande|Set SAFETY Commande|  
|Set SCOREBOARD Commande|Set SECONDS Commande|Set SEPARATOR Commande|  
|Set SHADOWS Commande|SET SKIP OF Command|Set SPACE Commande|  
|Set STATUS Commande|SET STATUS BAR Commande|Set STEP Commande|  
|SET STICKY Commande|Set SYSFORMATS Commande|SET SYSMENU Commande|  
|Set TALK Commande|SET TEXTMERGE Commande|SET TEXTMERGE DELIMITERS Commande|  
|Set TOPIC Commande|SET TOPIC ID Commande|SET TRBETWEEN Commande|  
|Set TYPEAHEAD Commande|Set VIEW Commande|SET WINDOW OF MEMO Command|  
|Set XCMDFILE Commande|_SHELL variable de mémoire du système|Commande SHOW GET|  
|Show GETS Commande|Commande SHOW MENU|Commande SHOW OBJECT|  
|Show POPUP Commande|Commande SHOW WINDOW|Commande SIZE POPUP|  
|Commande SIZE WINDOW|SKPBAR( ) Fonction|SKPPAD) ) Fonction|  
|SOUNDEX( ) Fonction|_SPELLCHK variable de mémoire du système|Fonctions SQL|  
|SROWS( ) Fonction|_STARTUP variable de mémoire du système|Commande SUSPEND|  
|Fonctions SYS() à l’exception de SYS(2011)|SYSMETRIC( ) Fonction||  
  
## <a name="t"></a>T  
  
||||  
|-|-|-|  
|_TABS variable de mémoire du système|Texte... Commande ENDTEXT|TXTWIDTH( ) Fonction|  
|TRANSFORM( ) Fonction|_TRANSPORT Variable de mémoire du système||  
|Commande TYPE|_THROTTLE variable de mémoire du système||  
  
## <a name="u"></a>U  
  
||||  
|-|-|-|  
|MISE À JOUR( ) Fonction|Commande USE||  
  
## <a name="v"></a>V  
  
||||  
|-|-|-|  
|Commande DATABASE VALIDATE|VARREAD( ) Fonction|VERSION( ) Fonction|  
  
## <a name="w"></a>W  
  
||||  
|-|-|-|  
|_WINDOWS variable de mémoire du système|_WIZARD Variable de mémoire du système|WCHILD( ) Fonction|  
|Commandement WAIT|WBORDER( ) Fonction|WFONT( ) Fonction|  
|WCOLS( ) Fonction|WEXIST( ) Fonction|WLROW( ) Fonction|  
|Avec... Commandement ENDWITH|WLAST( ) Fonction|WONTOP( ) Fonction|  
|WMAXIMUM( ) Fonction|WLCOL( ) Fonction|WREAD( ) Fonction|  
|WOUTPUT( ) Fonction|WMINIMUM( ) Fonction|WVISIBLE( ) Fonction|  
|WPARENT( ) Fonction|WTITLE( ) Fonction||  
|WROWS( ) Fonction|_WRAP Variable de mémoire du système||  
  
## <a name="z"></a>Z  
  
||||  
|-|-|-|  
|Commande ZOOM WINDOW|||
