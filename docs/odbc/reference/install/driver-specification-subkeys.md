---
title: Subkeys de spécification du conducteur (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280579"
---
# <a name="driver-specification-subkeys"></a>Sous-clés de spécification de pilote
Chaque pilote répertorié dans le sous-clé ODBC Drivers a une sous-clé de son propre. Ce sous-clé a le même nom que la valeur correspondante sous le sous-clé ODBC Drivers. Les valeurs sous cette sous-liste sont les chemins complets des DLL d’installation du conducteur et du conducteur, les valeurs des mots clés du conducteur retournés par **SQLDrivers**et le nombre d’utilisation. Les formats des valeurs sont tels qu’indiqués dans le tableau suivant.  
  
|Nom|Type de données|Données|  
|----------|---------------|----------|  
|APILevel|REG_SZ|**0** &#124; **1** &#124; **2**|  
|ConnectFunctions|REG_SZ|**Y**&#124;**N****Y**&#124;**N****Y**&#124;**N**|  
|CreateDSN|REG_SZ|*description du conducteur*|  
|Pilote|REG_SZ|*conducteur-DLL-chemin*|  
|DriverODBCVer|REG_SZ|*nn.nn (nn.nn)*|  
|FileExtns|REG_SZ|**\*.** *extension du fichier1*[**\*, .** *extension du fichier2*] ...|  
|FileUsage (en)|REG_SZ|**0** &#124; **1** &#124; **2**|  
|Programme d’installation|REG_SZ|*configuration-DLL-chemin*|  
|SQLLevel (SQLLevel)|REG_SZ|**0** &#124; **1** &#124; **2**|  
|UtilisationCompte|REG_DWORD|*count*|  
  
 L’utilisation de chaque mot clé est affichée dans le tableau suivant.  
  
|Mot clé|Usage|  
|-------------|-----------|  
|**APILevel**|Un numéro indiquant le niveau de conformité à l’interface ODBC pris en charge par le conducteur :<br /><br /> 0 = Aucun<br /><br /> 1 - Niveau 1 pris en charge<br /><br /> 2 - Niveau 2 pris en charge<br /><br /> Cela doit être le même que la valeur retournée pour l’option SQL_ODBC_INTERFACE_CONFORMANCE dans **SQLGetInfo**.|  
|**CreateDSN**|Le nom d’une ou plusieurs sources de données à créer lors de l’installation du pilote. Les informations du système doivent inclure une section de spécifications source de données pour chaque source de données répertoriée avec le mot clé **CreateDSN.** Ces sections ne doivent pas inclure le mot-clé **du pilote,** car cela est spécifié dans la section de spécification du conducteur, mais doit inclure suffisamment d’informations pour la fonction **ConfigDSN** dans la configuration du conducteur DLL pour créer une spécification source de données sans afficher de boîtes de dialogue. Pour le format d’une section de spécifications source de données, voir [Les sous-clés de spécifications de source de données](../../../odbc/reference/install/data-source-specification-subkeys.md).|  
|**ConnectFunctions**|Une chaîne à trois caractères indiquant si le conducteur prend en charge **SQLConnect**, **SQLDriverConnect**, et **SQLBrowseConnect**. Si le conducteur prend en charge **SQLConnect**, le premier personnage est "Y"; sinon, c’est "N". Si le conducteur prend en charge **SQLDriverConnect**, le deuxième personnage est "Y"; sinon, c’est "N". Si le conducteur prend en charge **SQLBrowseConnect**, le troisième personnage est "Y"; sinon, c’est "N". Par exemple, si un conducteur prend en charge **SQLConnect** et **SQLDriverConnect** mais pas **SQLBrowseConnect**, la chaîne à trois caractères est "YYN".|  
|**DriverODBCVer**|Une chaîne de caractères avec la version d’ODBC que le conducteur prend en charge. La version est de la forme *nn.nn*, où les deux premiers chiffres sont la version principale et les deux prochains chiffres sont la version mineure. Pour la version de l’ODBC décrite dans ce manuel, le conducteur doit retourner "03.00".<br /><br /> Cela doit être le même que la valeur retournée pour l’option SQL_DRIVER_ODBC_VER dans **SQLGetInfo**.|  
|**FileExtns**|Pour les pilotes basés sur les fichiers, une liste d’extensions séparées par virgule des fichiers que le conducteur peut utiliser. Par exemple, un pilote \*dBASE peut spécifier .dbf et un pilote de fichier texte formaté peut spécifier \*.txt,\*.csv. Pour un exemple de la façon dont une application peut utiliser ces informations, consultez le mot clé **FileUsage.**|  
|**FileUsage (en)**|Un numéro indiquant comment un pilote basé sur un fichier traite directement les fichiers dans une source de données.<br /><br /> 0 - Le conducteur n’est pas un conducteur basé sur le fichier. Par exemple, un pilote ORACLE est un pilote basé sur DBMS.<br /><br /> 1 - Un pilote basé sur des fichiers traite les fichiers dans une source de données comme des tableaux. Par exemple, un pilote Xbase traite chaque fichier Xbase comme une table.<br /><br /> 2 - Un pilote basé sur des fichiers traite les fichiers d’une source de données comme un catalogue. Par exemple, un pilote Microsoft® Access traite chaque fichier Microsoft Access comme une base de données complète.<br /><br /> Une application peut l’utiliser pour déterminer comment les utilisateurs sélectionneront les données. Par exemple, les utilisateurs de Xbase et Paradox pensent souvent que les données sont stockées dans les fichiers, tandis que les utilisateurs d’ORACLE et de Microsoft Access pensent généralement que les données sont stockées dans les tables.<br /><br /> Lorsqu’un utilisateur sélectionne **le fichier de données ouverts** dans le menu **Fichier,** une application peut afficher la boîte de dialogue commune **de Windows File Open.** La liste des types de fichiers utiliserait les extensions de fichiers spécifiées avec le mot clé **FileExtns** pour les pilotes qui spécifient une valeur **FileUsage** de 1 et "Y" comme deuxième caractère de la valeur du mot clé **ConnectFunctions.** Une fois que l’utilisateur a choisi un fichier, l’application appelle **SQLDriverConnect** avec le mot clé **DRIVER,** puis exécuterait une déclaration **DE nom de \* *table* SELECT FROM.**<br /><br /> Lorsque l’utilisateur sélectionne **les données d’importation** du menu **Fichier,** une application peut afficher une liste de descriptions pour les pilotes qui spécifient une valeur **De FileUsage** de 0 ou 2, et « Y » comme deuxième caractère de la valeur du mot clé **ConnectFunctions.** Une fois que l’utilisateur sélectionne un pilote, l’application appelle **SQLDriverConnect** avec le mot-clé **DRIVER,** puis afficherait une boîte de dialogue **Select Table** personnalisée.|  
|**SQLLevel (SQLLevel)**|Un numéro indiquant la grammaire SQL-92 supportée par le conducteur :<br /><br /> 0 - SQL-92 Entrée<br /><br /> 1 - FIPS127-2 Transition<br /><br /> 2 - SQL-92 Intermédiaire<br /><br /> 3 - SQL-92 Complet<br /><br /> Cela doit être le même que la valeur retournée pour l’option SQL_SQL_CONFORMANCE dans **SQLGetInfo**.|  
  
 Pour plus d’informations sur les comptes d’utilisation, voir [Compter l’utilisation](../../../odbc/reference/install/usage-counting.md) plus tôt dans cette section.  
  
 Les applications ne doivent pas définir le nombre d’utilisations. ODBC maintiendra ce décompte.  
  
 Par exemple, supposons qu’un pilote pour les fichiers texte formatés a un pilote DLL nommé Text.dll, une configuration de pilote séparée DLL nommé Txtsetup.dll, et a été installé trois fois. Si le conducteur prend en charge le niveau de conformité API de niveau 1, prend en charge le niveau minimum de conformité à la grammaire SQL, traite les fichiers comme des tableaux et peut utiliser des fichiers avec les extensions .txt et .csv, les valeurs sous le sous-clé de texte peuvent être les suivantes :  
  
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
