---
title: Sous-clés de spécification de pilote | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC], driver specification subkeys
- driver specification subkeys [ODBC]
- registry entries for components [ODBC], driver specification subkeys
- drivers subkey [ODBC]
ms.assetid: b4d802ef-b199-4e64-b7a5-6f2b3e5e2c80
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 47aa75f647e5fd8a88168611a3b21284962c70a4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280579"
---
# <a name="driver-specification-subkeys"></a>Sous-clés de spécification de pilote
Chaque pilote figurant dans la sous-clé pilotes ODBC a sa propre sous-clé. Cette sous-clé porte le même nom que la valeur correspondante sous la sous-clé ODBC Drivers. Les valeurs de cette sous-clé répertorient les chemins complets des dll d’installation du pilote et du pilote, les valeurs des mots clés du pilote retournés par **SQLDrivers**et le nombre d’utilisations. Les formats des valeurs sont répertoriés dans le tableau suivant.  
  
|Nom|Type de données|Données|  
|----------|---------------|----------|  
|APILevel|REG_SZ|**0** &#124; **1** &#124; **2**|  
|ConnectFunctions|REG_SZ|{**Y**&#124;**n**} {**y**&#124;**n**} {**y**&#124;**N**}|  
|CreateDSN|REG_SZ|*Description du pilote*|  
|Pilote|REG_SZ|*Driver-DLL-Path*|  
|DriverODBCVer|REG_SZ|*nn. nn*|  
|FileExtns|REG_SZ|**\*.** *fichier-extension1*[**,\*.** *fichier-extension2*] ...|  
|FileUsage|REG_SZ|**0** &#124; **1** &#124; **2**|  
|Programme d’installation|REG_SZ|*Setup-DLL-Path*|  
|SQLLevel|REG_SZ|**0** &#124; **1** &#124; **2**|  
|UsageCount|REG_DWORD|*count*|  
  
 L’utilisation de chaque mot clé est indiquée dans le tableau suivant.  
  
|Mot clé|Usage|  
|-------------|-----------|  
|**APILevel**|Nombre indiquant le niveau de conformité de l’interface ODBC pris en charge par le pilote :<br /><br /> 0 = Aucun<br /><br /> 1 = niveau 1 pris en charge<br /><br /> 2 = niveau 2 pris en charge<br /><br /> Ce doit être identique à la valeur retournée pour l’option SQL_ODBC_INTERFACE_CONFORMANCE dans **SQLGetInfo**.|  
|**CreateDSN**|Nom d’une ou plusieurs sources de données à créer lors de l’installation du pilote. Les informations système doivent inclure une section de spécification de source de données pour chaque source de données listée avec le mot clé **CreateDSN** . Ces sections ne doivent pas inclure le mot clé **Driver** , car celles-ci sont spécifiées dans la section Spécification du pilote, mais elles doivent inclure suffisamment d’informations pour la fonction **CONFIGDSN** dans la dll d’installation du pilote pour créer une spécification de source de données sans afficher de boîtes de dialogue. Pour le format d’une section de spécification de source de données, consultez [sous-clés de spécification de source de données](../../../odbc/reference/install/data-source-specification-subkeys.md).|  
|**ConnectFunctions**|Chaîne de trois caractères indiquant si le pilote prend en charge **SQLConnect**, **SQLDriverConnect**et **SQLBrowseConnect**. Si le pilote prend en charge **SQLConnect**, le premier caractère est « Y »; dans le cas contraire, il s’agit de « N ». Si le pilote prend en charge **SQLDriverConnect**, le deuxième est « Y ». dans le cas contraire, il s’agit de « N ». Si le pilote prend en charge **SQLBrowseConnect**, le troisième caractère est « Y »; dans le cas contraire, il s’agit de « N ». Par exemple, si un pilote prend en charge **SQLConnect** et **SQLDriverConnect** , mais pas **SQLBrowseConnect**, la chaîne de trois caractères est « YYN ».|  
|**DriverODBCVer**|Chaîne de caractères avec la version d’ODBC que le pilote prend en charge. La version se présente sous la forme *nn. NN*, où les deux premiers chiffres correspondent à la version principale et les deux chiffres suivants à la version mineure. Pour la version de ODBC décrite dans ce manuel, le pilote doit retourner « 03,00 ».<br /><br /> Ce doit être identique à la valeur retournée pour l’option SQL_DRIVER_ODBC_VER dans **SQLGetInfo**.|  
|**FileExtns**|Pour les pilotes basés sur des fichiers, liste séparée par des virgules des extensions des fichiers que le pilote peut utiliser. Par exemple, un pilote dBASE peut spécifier \*. DBF et un pilote de fichier texte mis en \*forme peut spécifier\*. txt,. csv. Pour obtenir un exemple de la façon dont une application peut utiliser ces informations, consultez le mot clé **FileUsage** .|  
|**FileUsage**|Nombre indiquant comment un pilote basé sur des fichiers traite directement des fichiers dans une source de données.<br /><br /> 0 = le pilote n’est pas un pilote basé sur des fichiers. Par exemple, un pilote ORACLE est un pilote SGBD.<br /><br /> 1 = un pilote basé sur des fichiers traite les fichiers d’une source de données en tant que tables. Par exemple, un pilote xbase traite chaque fichier xbase comme une table.<br /><br /> 2 = un pilote basé sur des fichiers traite les fichiers d’une source de données comme un catalogue. Par exemple, un pilote Microsoft® Access traite chaque fichier Microsoft Access comme une base de données complète.<br /><br /> Une application peut l’utiliser pour déterminer la manière dont les utilisateurs sélectionnent les données. Par exemple, les utilisateurs xbase et Paradox considèrent souvent les données comme stockées dans des fichiers, tandis que les utilisateurs ORACLE et Microsoft Access considèrent généralement les données comme stockées dans les tables.<br /><br /> Lorsqu’un utilisateur sélectionne **ouvrir un fichier de données** dans le menu **fichier** , une application peut afficher la boîte de dialogue Ouvrir un fichier commun de **Windows** . La liste des types de fichiers utilise les extensions de fichier spécifiées avec le mot clé **FileExtns** pour les pilotes qui spécifient une valeur **FileUsage** de 1 et « Y » comme deuxième caractère de la valeur du mot clé **ConnectFunctions** . Une fois que l’utilisateur a sélectionné un fichier, l’application appelle **SQLDriverConnect** avec le mot clé **Driver** , puis exécute une instruction **Select \* from *table-Name* ** .<br /><br /> Quand l’utilisateur sélectionne **importer des données** à partir du menu **fichier** , une application peut afficher une liste de descriptions pour les pilotes qui spécifient une valeur **FileUsage** de 0 ou 2, et « Y » comme deuxième caractère de la valeur du mot clé **ConnectFunctions** . Une fois que l’utilisateur a sélectionné un pilote, l’application appelle **SQLDriverConnect** avec le mot clé **Driver** , puis affiche une boîte de dialogue **Sélectionner une table** personnalisée.|  
|**SQLLevel**|Nombre indiquant la grammaire SQL-92 prise en charge par le pilote :<br /><br /> 0 = entrée SQL-92<br /><br /> 1 = FIPS127-2 transitoire<br /><br /> 2 = SQL-92 intermédiaire<br /><br /> 3 = SQL-92 complet<br /><br /> Ce doit être identique à la valeur retournée pour l’option SQL_SQL_CONFORMANCE dans **SQLGetInfo**.|  
  
 Pour plus d’informations sur le nombre d’utilisations, consultez [utilisation du comptage](../../../odbc/reference/install/usage-counting.md) plus haut dans cette section.  
  
 Les applications ne doivent pas définir le nombre d’utilisations. ODBC conservera ce nombre.  
  
 Par exemple, supposons qu’un pilote pour les fichiers texte mis en forme a une DLL de pilote nommée Text. dll, une DLL de configuration de pilote distincte nommée Txtsetup. dll et a été installée trois fois. Si le pilote prend en charge le niveau de conformité de l’API de niveau 1, prend en charge le niveau de conformité de la grammaire SQL minimale, traite les fichiers comme des tables et peut utiliser des fichiers avec les extensions. txt et. csv, les valeurs sous la sous-clé de texte peuvent se présenter comme suit :  
  
```  
APILevel : REG_SZ : 1  
ConnectFunctions : REG_SZ : YYN  
Driver : REG_SZ : C:\WINDOWS\SYSTEM32\TEXT.DLL  
DriverODBCVer : REG_SZ : 03.00.00  
FileExtns : REG_SZ : *.txt,*.csv  
FileUsage : REG_SZ : 1  
Setup : REG_SZ : C:\WINDOWS\SYSTEM32\TXTSETUP.DLL  
SQLLevel : REG_SZ : 0  
UsageCount : REG_DWORD : 0x3  
```
