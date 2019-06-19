---
title: ODBCCONF.EXE | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- odbcconf.exe
ms.assetid: 3bf2be83-61f9-4183-836b-85204ac7116a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2b4d7b20c690a1f4d7f3b445afb8348549309e5c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65538210"
---
# <a name="odbcconfexe"></a>ODBCCONF.EXE
ODBCCONF.exe est un outil de ligne de commande qui vous permet de configurer des noms de source de données et les pilotes ODBC.  
  
> [!NOTE]  
>  ODBCCONF.exe sera supprimée dans une future version de Windows Data Access Components. Évitez d’utiliser cette fonctionnalité et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Vous pouvez utiliser les commandes PowerShell pour gérer les pilotes et les sources de données. Pour plus d’informations sur ces commandes PowerShell, consultez [applets de commande Windows Data Access Components](https://technet.microsoft.com/library/hh771019.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
ODBCCONF [switches] action  
```  
  
## <a name="arguments"></a>Arguments  
 *switches*  
 Zéro ou plusieurs options de commutateur. Pour la liste des commutateurs disponibles, consultez la section Notes, plus loin dans cette rubrique.  
  
 *action*  
 Une action à effectuer. Pour la liste des options disponibles, consultez la section Notes.  
  
## <a name="remarks"></a>Notes  
 Les commutateurs suivants sont disponibles :  
  
|Basculer|Description|  
|------------|-----------------|  
|/A {*action*}|Spécifiez une action.<br /><br /> /A est facultative si seule une action est spécifiée.|  
|/?|Afficher l’utilisation pour ODBCCONF. EXE.|  
|/C|Le traitement se poursuit si une action échoue.|  
|/E|Effacer le fichier de réponse spécifié avec /F lorsque le traitement est terminé.|  
|/F|Utiliser un fichier réponse, tel que `odbcconf /F my.rsp`.<br /><br /> My.rsp peut se présenter comme suit : `REGSVR c:\my.dll`<br /><br /> /A n’est pas utilisé dans un fichier réponse.|  
|/H|Afficher l’utilisation (aide). Ce commutateur est identique à / ?.|  
|/L[*mode*] *filename*|Envoyer la sortie du programme dans un fichier dans un des trois modes : normal (n), verbose (v) et le débogage (d). Les DLL qui sont chargés par odbcconf.exe enregistrements du mode de débogage.<br /><br /> Si vous spécifiez/l sans mode, le fichier journal sera vide.<br /><br /> Par exemple, **/Lv log.txt**.|  
|/R|L’action sera effectuée après un redémarrage.|  
|/S|Mode silencieux. Ne pas afficher les messages d’erreur.|  
  
 Les actions suivantes sont disponibles :  
  
|Action|Description|  
|------------|-----------------|  
|CONFIGDRIVER *nom_pilote ** configuration spécifique au pilote params*|Charge la DLL d’installation du pilote approprié et appelle le **ConfigDriver** (fonction).<br /><br /> Équivalent à la [sqlconfigdriver, fonction](../odbc/reference/syntax/sqlconfigdriver-function.md).<br /><br /> Exemple :<br /><br /> /A {CONFIGDRIVER « Nom du pilote » « CPTimeout = 60 »}<br /><br /> /A {CONFIGDRIVER « Nom du pilote » « DriverODBCVer = 03.80 »}|  
|CONFIGDSN *nom_pilote* DSN =*nom* &#124; *attributs*|Ajoute ou modifie une source de données système.<br /><br /> Équivalent à la [fonction SQLConfigDataSource](../odbc/reference/syntax/sqlconfigdatasource-function.md).<br /><br /> Exemple :<br /><br /> /A {CONFIGDSN "SQL Server" "DSN=name &#124; Server=srv"}|  
|CONFIGSYSDSN *driver_name* DSN=*name* &#124; *attributes*|Ajoute ou modifie une source de données système.<br /><br /> Équivalent à la [fonction SQLConfigDataSource](../odbc/reference/syntax/sqlconfigdatasource-function.md).<br /><br /> Exemple :<br /><br /> /A {CONFIGSYSDSN "SQL Server" "DSN=name &#124; Server=srv"}|  
|/INSTALLDRIVER|Équivalent à [sqlinstalldriverex, fonction](../odbc/reference/syntax/sqlinstalldriverex-function.md).<br /><br /> Pour plus d’informations sur la syntaxe de paires mot clé-valeur passée à /INSTALLDRIVER, consultez [sous-clés de spécification de pilote](../odbc/reference/install/driver-specification-subkeys.md).<br /><br /> Exemple :<br /><br /> /A {INSTALLDRIVER  "Your Driver &#124; Driver=c:\your.dll &#124; Setup=c:\your.dll &#124; APILevel=2 &#124; ConnectFunctions=YYY &#124; DriverODBCVer=03.50 &#124; FileUsage=0 &#124; SQLLevel=1"}|  
|INSTALLTRANSLATOR *configuration du traducteur ** chemin d’accès du pilote*|Ajoute des informations sur un traducteur pour le **HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCINST. INI\ODBC traducteurs** clé de Registre.<br /><br /> Équivalent à [sqlinstalltranslatorex, fonction](../odbc/reference/syntax/sqlinstalltranslatorex-function.md).<br /><br /> Pour plus d’informations sur la syntaxe de paires mot clé-valeur passée à /INSTALLDRIVER, consultez [sous-clés de spécification de traducteur](../odbc/reference/install/translator-specification-subkeys.md).<br /><br /> Exemple :<br /><br /> /A {INSTALLTRANSLATOR  "My Translator &#124; Translator=c:\my.dll &#124; Setup=c:\my.dll"}|  
|REGSVR *dll*|Inscrit une DLL.<br /><br /> Équivalent de regsvr32.exe.<br /><br /> Exemple :<br /><br /> /A {REGSVR c:\my.dll}|  
|SETFILEDSNDIR|Lorsque HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBC. INI\ODBC fichier DSN\DefaultDSNDir n’existe pas, l’action SETFILEDSNDIR crée et affectez-lui la valeur à HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\CommonFilesDir, ajouté avec \ODBC\Data Sources.<br /><br /> Valeur à HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBC. INI\ODBC fichier DSN\DefaultDSNDir Spécifie l’emplacement par défaut utilisé par l’administrateur de sources de données ODBC lors de la création d’une source de données de fichiers.<br /><br /> Exemple :<br /><br /> /A {SETFILEDSNDIR}|  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft ODBC (Open Database Connectivity)](../odbc/microsoft-open-database-connectivity-odbc.md)
