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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b15aa278e2fe38afe93f5628433a6c8f4b41cd8e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63198321"
---
# <a name="driver-specification-subkeys"></a>Sous-clés de spécification de pilote
Chaque pilote répertorié dans la sous-clé de pilotes ODBC a une sous-clé de son propre. Cette sous-clé a le même nom que la valeur correspondante sous la sous-clé de pilotes ODBC. Les valeurs sous cette sous-clé de répertorient les chemins d’accès complets du pilote et de la configuration du pilote DLL, les valeurs des mots clés du pilote retournés par **SQLDrivers**et le décompte d’utilisation. Les formats des valeurs sont comme indiqué dans le tableau suivant.  
  
|Nom|Type de données|Données|  
|----------|---------------|----------|  
|APILevel|REG_SZ|**0** &#124; **1** &#124; **2**|  
|ConnectFunctions|REG_SZ|{**Y**&#124;**N**}{**Y**&#124;**N**}{**Y**&#124;**N**}|  
|CreateDSN|REG_SZ|*driver-description*|  
|Pilote|REG_SZ|*driver-DLL-path*|  
|DriverODBCVer|REG_SZ|*nn.nn*|  
|FileExtns|REG_SZ|**\*.** *file-extension1*[ **,\*.** *file-extension2*]...|  
|FileUsage|REG_SZ|**0** &#124; **1** &#124; **2**|  
|Installation|REG_SZ|*setup-DLL-path*|  
|SQLLevel|REG_SZ|**0** &#124; **1** &#124; **2**|  
|UsageCount|REG_DWORD|*nombre*|  
  
 L’utilisation de chaque mot clé est indiquée dans le tableau suivant.  
  
|Mot clé|Utilisation|  
|-------------|-----------|  
|**APILevel**|Un nombre indiquant la ODBC pris en charge par le pilote de niveau de conformité de l’interface :<br /><br /> 0 = Aucun<br /><br /> 1 = 1 niveau pris en charge<br /><br /> 2 = niveau 2 est pris en charge<br /><br /> Cela doit être identique à la valeur retournée pour l’option SQL_ODBC_INTERFACE_CONFORMANCE dans **SQLGetInfo**.|  
|**CreateDSN**|Le nom d’une ou plusieurs sources de données doit être créé lorsque le pilote est installé. Les informations système doivent inclure une section de spécification de source de données pour chaque source de données répertorié avec le **CreateDSN** mot clé. Ces sections ne doivent pas inclure le **pilote** mot clé, car cela est spécifié dans la section de la spécification du pilote, mais que vous devez inclure suffisamment d’informations pour le **ConfigDSN** dans le pilote (fonction) DLL pour créer une spécification de source de données sans afficher les boîtes de dialogue d’installation. Pour le format d’une section de spécification de source de données, consultez [sous-clés de spécification de Source de données](../../../odbc/reference/install/data-source-specification-subkeys.md).|  
|**ConnectFunctions**|Une chaîne de trois caractères qui indique si le pilote prend en charge **SQLConnect**, **SQLDriverConnect**, et **SQLBrowseConnect**. Si le pilote prend en charge **SQLConnect**, le premier caractère est « Y » ; sinon, il est « N ». Si le pilote prend en charge **SQLDriverConnect**, le deuxième caractère est « Y » ; sinon, il est « N ». Si le pilote prend en charge **SQLBrowseConnect**, le troisième caractère est « Y » ; sinon, il est « N ». Par exemple, si un pilote prend en charge **SQLConnect** et **SQLDriverConnect** mais pas **SQLBrowseConnect**, la chaîne de trois caractères est « YYN ».|  
|**DriverODBCVer**|Une chaîne de caractères avec la version d’ODBC qui prend en charge par le pilote. La version est au format *nn.nn*, où les deux premiers chiffres sont la version principale et les deux chiffres suivants à la version mineure. Pour la version d’ODBC, décrit dans ce manuel, le pilote doit retourner « 03.00 ».<br /><br /> Cela doit être identique à la valeur retournée pour l’option SQL_DRIVER_ODBC_VER dans **SQLGetInfo**.|  
|**FileExtns**|Pour les pilotes basés sur fichier, une liste séparée par des virgules des extensions des fichiers le pilote peut utiliser. Par exemple, un pilote dBASE peut spécifier \*.dbf et un pilote de fichier texte mis en forme peuvent spécifier \*.txt,\*.csv. Pour obtenir un exemple de la façon dont une application peut utiliser ces informations, consultez le **FileUsage** mot clé.|  
|**FileUsage**|Nombre indiquant la manière dont un pilote basé sur fichier traite directement les fichiers dans une source de données.<br /><br /> 0 = le pilote n’est pas un pilote basé sur fichier. Par exemple, un pilote ORACLE est un pilote de SGBD.<br /><br /> 1 = fichiers traite pilote basé sur le fichier dans une source de données en tant que tables. Par exemple, un pilote Xbase traite chaque fichier Xbase sous forme de table.<br /><br /> 2 = un pilote basé sur fichier traite les fichiers dans une source de données en tant que catalogue. Par exemple, un pilote Microsoft® Access traite chaque fichier Microsoft Access comme une base de données complète.<br /><br /> Une application peut utiliser cela pour déterminer la façon dont les utilisateurs sélectionnera les données. Par exemple, les utilisateurs Xbase et Paradox pensent souvent des données stockées dans des fichiers, tandis que les utilisateurs ORACLE et Microsoft Access pensent généralement de données tel que stocké dans les tables.<br /><br /> Lorsqu’un utilisateur sélectionne **ouvrir un fichier données** à partir de la **fichier** menu, une application peut afficher le **Windows File Open** boîte de dialogue commune. La liste des types de fichiers utiliserait les extensions de fichier spécifiées avec le **FileExtns** mot clé pour les pilotes qui spécifient un **FileUsage** valeur de 1 et « Y » en tant que le deuxième caractère de la valeur de la  **ConnectFunctions** mot clé. Une fois que l’utilisateur sélectionne un fichier, l’application appelle **SQLDriverConnect** avec la **pilote** mot clé, puis exécutez un **sélectionnez \* FROM *-nom de la table***   instruction.<br /><br /> Lorsque l’utilisateur sélectionne **importer des données** à partir de la **fichier** menu, une application peut afficher une liste de descriptions pour les pilotes qui spécifient un **FileUsage** valeur égale à 0 ou 2 « Y » comme le deuxième caractère de la valeur de la **ConnectFunctions** mot clé. Une fois que l’utilisateur sélectionne un pilote, l’application appelle **SQLDriverConnect** avec la **pilote** puis affichage personnalisé et mot clé **sélectionner une Table** boîte de dialogue.|  
|**SQLLevel**|Nombre indiquant la grammaire SQL-92 pris en charge par le pilote :<br /><br /> 0 = entrée SQL-92<br /><br /> 1 = transitoire FIPS127-2<br /><br /> 2 = SQL-92 intermédiaire<br /><br /> 3 = SQL-92 Full<br /><br /> Cela doit être identique à la valeur retournée pour l’option SQL_SQL_CONFORMANCE dans **SQLGetInfo**.|  
  
 Pour plus d’informations sur les compteurs d’utilisation, consultez [nombre d’utilisations](../../../odbc/reference/install/usage-counting.md) plus haut dans cette section.  
  
 Applications ne doivent pas définir le décompte d’utilisation. ODBC gère ce nombre.  
  
 Par exemple, supposons qu’un pilote pour les fichiers de texte mis en forme a un DLL nommée Text.dll du pilote, un programme d’installation de pilote séparé DLL nommé Txtsetup.dll et a été installé trois fois. Si le pilote prend en charge le niveau de conformité de niveau 1 API prend en charge le niveau de conformité de grammaire SQL minimale, traite les fichiers en tant que tables et peut utiliser des fichiers avec les extensions .txt et .csv, il se peut que les valeurs sous la sous-clé de texte peuvent être comme suit :  
  
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
