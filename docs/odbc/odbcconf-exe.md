---
title: ODBCCONF. EXE - France Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d771f01d292312f8a0f0060c16e3c348bf2e009e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307530"
---
# <a name="odbcconfexe"></a>ODBCCONF. EXE (EXE)
ODBCCONF.exe est un outil de ligne de commande qui vous permet de configurer les pilotes ODBC et les noms de source de données.  
  
> [!NOTE]  
>  ODBCCONF.exe sera supprimé dans une future version des composants d’accès aux données Windows. Évitez d’utiliser cette fonctionnalité et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Vous pouvez utiliser les commandes PowerShell pour gérer les pilotes et les sources de données. Pour plus d’informations sur ces commandes PowerShell, voir [Windows Data Access Components cmdlets](/powershell/module/wdac).  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
ODBCCONF [switches] action  
```  
  
## <a name="arguments"></a>Arguments  
 *Commutateurs*  
 Zéro ou plus d’options de commutation. Pour la liste des commutateurs disponibles, voir la section Remarques, plus tard dans ce sujet.  
  
 *action*  
 Une action à effectuer. Pour la liste des options disponibles, consultez la section Remarques.  
  
## <a name="remarks"></a>Notes  
 Les commutateurs suivants sont disponibles :  
  
|Commutateur|Description|  
|------------|-----------------|  
|/A*action*|Spécifier une action.<br /><br /> /A est facultatif si une seule action est spécifiée.|  
|/?|Utilisation de l’affichage pour ODBCCONF. EXE, C’EST EXE.|  
|/C|Le traitement se poursuit en cas d’échec d’une action.|  
|/E|Effacer le fichier de réponse spécifié avec /F lorsque le traitement est terminé.|  
|/F|Utilisez un fichier de `odbcconf /F my.rsp`réponse, tel que .<br /><br /> my.rsp pourrait ressembler à ceci:`REGSVR c:\my.dll`<br /><br /> /A n’est pas utilisé dans un fichier de réponse.|  
|/H|Utilisation de l’affichage (Aide). Ce commutateur est le même que /?.|  
|/L[*mode*] *nom de fichier*|Envoyer la sortie du programme à un fichier dans l’un des trois modes: normal (n), verbeux (v), et débog (d). Le mode Debug enregistre les DLL qui sont chargés par odbcconf.exe.<br /><br /> Si vous spécifiez /L sans mode, le fichier journal sera vide.<br /><br /> Par exemple, **/Lv log.txt**.|  
|/R|L’action sera effectuée après un redémarrage.|  
|/S|Mode silencieux. N’affichez pas de messages d’erreur.|  
  
 Les actions suivantes sont disponibles :  
  
|Action|Description|  
|------------|-----------------|  
|LES *parames de configuration spécifiques à l’driver_name-conducteur de* CONFIGDRIVER|Charge la configuration appropriée du pilote DLL et appelle la fonction **ConfigDriver.**<br /><br /> Équivalent à la [fonction SQLConfigDriver](../odbc/reference/syntax/sqlconfigdriver-function.md).<br /><br /> Par exemple :<br /><br /> /A 'CONFIGDRIVER " Nom du conducteur' "CPTimeout'60"<br /><br /> /A 'CONFIGDRIVER " Nom du conducteur' "DriverODBCVer'03.80"|  
|CONFIGDSN *driver_name* *nom* DSND &#124; *attributs*|Ajoute ou modifie une source de données système.<br /><br /> Équivalent à la [fonction SQLConfigDataSource](../odbc/reference/syntax/sqlconfigdatasource-function.md).<br /><br /> Par exemple :<br /><br /> /A 'CONFIGDSN "SQL Server" "DSN-name &#124; Server’srv"|  
|CONFIGSYSDSN *driver_name* *nom* DSND &#124; *attributs*|Ajoute ou modifie une source de données système.<br /><br /> Équivalent à la [fonction SQLConfigDataSource](../odbc/reference/syntax/sqlconfigdatasource-function.md).<br /><br /> Par exemple :<br /><br /> /A 'CONFIGSYSDSN "SQL Server" "DSN-name &#124; Server’srv"|  
|INSTALLDRIVER (EN)|Équivalent à [SQLInstallDriverEx Fonction](../odbc/reference/syntax/sqlinstalldriverex-function.md).<br /><br /> Pour plus d’informations sur la syntaxe des paires de mots-clés transmises à INSTALLDRIVER, voir [Subkeys de spécification du conducteur](../odbc/reference/install/driver-specification-subkeys.md).<br /><br /> Par exemple :<br /><br /> /A 'INSTALLDRIVER " Votre pilote &#124; Driver’c:-your.dll &#124; Setup-c:-your.dll &#124; APILevel-2 &#124; ConnectFunctions-YYY &#124; DriverODBCVer-03.50 &#124; FileUsageMD 0 &#124; SQLLevel-1".|  
|CONFIGURATION de traducteur INSTALLTRANSLATOR *-trajectoire de pilote*|Ajoute des informations sur un traducteur à la **HKEY_LOCAL_MACHINE-SOFTWARE-ODBC-ODBCINST. Clé de registre des traducteurs INI-ODBC.**<br /><br /> Équivalent à [SQLInstallTranslatorEx Fonction](../odbc/reference/syntax/sqlinstalltranslatorex-function.md).<br /><br /> Pour plus d’informations sur la syntaxe des paires de mots-clés transmises à INSTALLDRIVER, voir [Subkeys de spécification de traducteur](../odbc/reference/install/translator-specification-subkeys.md).<br /><br /> Par exemple :<br /><br /> /A 'INSTALLTRANSLATOR" Mon traducteur &#124; Traducteur’c: 'my.dll &#124; Setup’c:'my.dll"|  
|Dll *dll* REGSVR|Enregistre un DLL.<br /><br /> Équivalent à regsvr32.exe.<br /><br /> Par exemple :<br /><br /> /A 'REGSVR c:'my.dll'|  
|SETFILEDSNDIR|Lorsqu’HKEY_LOCAL_MACHINE-SOFTWARE-ODBC-ODBC. Le fichier DSN-DefaultDSNDir n’existe pas, l’action SETFILEDSNDIR la créera et lui attribuera la valeur à HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-Windows-CurrentVersion-CommonFilesDir, annexée par les sources de données d’ODBC.<br /><br /> La valeur à HKEY_LOCAL_MACHINE-SOFTWARE-ODBC-ODBC. Le fichier DSN-DefaultDSNDir specifie l’emplacement par défaut utilisé par l’administrateur de source de données ODBC lors de la création d’une source de données basée sur des fichiers.<br /><br /> Par exemple :<br /><br /> /UN SETFILEDSNDIR|  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft ODBC (Open Database Connectivity)](../odbc/microsoft-open-database-connectivity-odbc.md)
