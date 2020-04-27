---
title: Informations sur la version et l’en-tête de base de données locale | SQL Server Express Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_location:
- sqluserinstance.dll
ms.assetid: 506b5161-b902-4894-b87b-9192d7b1664a
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 6e390430115daf394c5e94267dad30a87851375d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63128697"
---
# <a name="sql-server-express-localdb-header-and-version-information"></a>En-tête et informations de version SQL Server Express LocalDB
  Il n'y a aucun fichier d'en-tête distinct pour l'API de l'instance de base de données locale SQL Server Express (LocalDB) ; les signatures de la fonction et les codes d'erreur de LocalDB sont définis dans le fichier d'en-tête SQL Server Native Client (sqlncli.h). Pour utiliser l'API d'instance de LocalDB, vous devez inclure le fichier d'en-tête sqlncli.h dans votre projet.  
  
## <a name="localdb-versioning"></a>Contrôle de version de LocalDB  
 L'installation de LocalDB utilise un jeu unique de binaires par version principale de SQL Server. Ces versions de LocalDB sont conservées et des correctifs de logiciel sont appliqués indépendamment. Cela signifie que l'utilisateur doit spécifier la version de base de LocalDB (autrement dit, la version principale de SQL Server) qu'il utilisera. La version est spécifiée dans le format de version standard défini par la classe .NET Framework **System. version** :  
  
 *Major. minor [. Build [. Revision]]*  
  
 Les deux premiers nombres dans la chaîne de version (*major* et *Minor*) sont obligatoires. Les deux derniers nombres dans la chaîne de version (*Build* et *révision*) sont facultatifs et la valeur par défaut est zéro si l’utilisateur les quitte. Cela signifie que si l’utilisateur spécifie uniquement « 12,2 » comme numéro de version de base de données locale, il est traité comme si l’utilisateur avait spécifié « 12.2.0.0 ».  
  
 La version pour l'installation de LocalDB est définie dans la clé de Registre MSSQLServer\CurrentVersion sous la clé de Registre de l'instance de SQL Server, par exemple :  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL12E.LOCALDB\ MSSQLServer\CurrentVersion: "CurrentVersion"="12.0.2531.0"  
```  
  
 Plusieurs versions de LocalDB sur la même station de travail sont prises en charge côte à côte. Toutefois, le code utilisateur utilise toujours la dernière dll **SQLUserInstance** disponible sur l’ordinateur local pour se connecter aux instances de base de données locale.  
  
## <a name="locating-the-sqluserinstance-dll"></a>Recherche de la DLL SQLUserInstance  
 Pour localiser la dll **SQLUserInstance** , le fournisseur client utilise la clé de Registre suivante :  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server Local DB\Installed Versions]  
```  
  
 Sous cette clé il existe une liste des clés, une pour chaque version de LocalDB installée sur l'ordinateur. Chacune de ces clés est nommée avec le numéro de version de la base de données locale au format * \<version principale>*.>de [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] *version mineure (par exemple, la clé de est nommée 12,0 \<* ). Sous chaque clé de version il existe des paires nom-valeur de `InstanceAPIPath` qui définissent le chemin d'accès complet au fichier de SQLUserInstance.dll installé avec cette version. L'exemple suivant illustre les entrées de Registre d'un ordinateur sur lequel les versions 11.0 et 12.0 de LocalDB sont installées :  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server Local DB\Installed Versions\12.0]  
"InstanceAPIPath"="C:\\Program Files\\Microsoft SQL Server\\120\\LocalDB\\Binn\\SqlUserInstance.dll"  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server Local DB\Installed Versions\12.0]  
"InstanceAPIPath"="C:\\Program Files\\Microsoft SQL Server\\120\\LocalDB\\Binn\\SqlUserInstance.dll"]  
```  
  
 Le fournisseur client doit trouver la version la plus récente parmi toutes les versions installées et charger le fichier dll `InstanceAPIPath` **SQLUserInstance** à partir de la valeur associée.  
  
### <a name="wow64-mode-on-64-bit-windows"></a>Mode WOW64 sur Windows 64 bits  
 Les installations 64 bits de LocalDB ont un jeu supplémentaire de clés de Registre pour permettre aux applications 32 bits s'exécutant en mode Windows-32-on-Windows-64 (WOW64) d'utiliser LocalDB. En particulier, sur Windows 64 bits, le fichier MSI de LocalDB crée les clés de Registre suivantes :  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wow6432Node\Microsoft SQL Server Local DB\Installed Versions\12.0]  
"InstanceAPIPath"="C:\\Program Files (x86)\\Microsoft SQL Server\\120\\LocalDB\\Binn\\SqlUserInstance.dll"  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wow6432Node\Microsoft SQL Server Local DB\Installed Versions\12.0]  
"InstanceAPIPath"="C:\\Program Files (x86)\\Microsoft SQL Server\\120\\LocalDB\\Binn\\SqlUserInstance.dll"]  
  
```  
  
 les programmes 64 bits qui lisent la clé voient `Installed Versions` les valeurs pointant vers les versions 64 bits de la dll **SQLUserInstance** , tandis que les programmes 32 bits (exécutés sur des fenêtres 64 bits en mode WOW64) sont automatiquement `Installed Versions` redirigés vers `Wow6432Node` une clé située sous la ruche. Cette clé contient des valeurs qui pointent vers les versions 32 bits de la dll **SQLUserInstance** .  
  
## <a name="using-localdb_define_proxy_functions"></a>Utilisation de LOCALDB_DEFINE_PROXY_FUNCTIONS  
 L’API d’instance de base de données locale définit une constante nommée LOCALDB_DEFINE_PROXY_FUNCTIONS qui automatise la découverte et le chargement de la dll **SqlUserInstance** .  
  
 La section de code activée par cette constante fournit une implémentation des proxys pour chacune des API de LocalDB. Les implémentations de proxy utilisent une fonction commune pour la liaison aux points d’entrée dans la dernière dll **SqlUserInstance** installée, puis transfèrent les requêtes.  
  
 Les fonctions de proxy ne sont activées que si la constante LOCALDB_DEFINE_PROXY_FUNCTIONS est définie dans le code utilisateur avant d'inclure le fichier sqlncli.h. La constante doit être définie dans un seul module source (fichier .cpp), car elle définit les noms de fonctions externes pour tous les points d'entrée d'API. Elle fournit une implémentation des proxys pour chacune des API de LocalDB.  
  
 L'exemple de code suivant montre comment utiliser la macro du code C++ natif :  
  
```  
// Define the LOCALDB_DEFINE_PROXY_FUNCTIONS constant to enable the LocalDB proxy functions   
// The #define has to take place BEFORE the API header file (sqlncli.h) is included  
#define LOCALDB_DEFINE_PROXY_FUNCTIONS  
#include <sqlncli.h>  
...  
HRESULT hr = S_OK;  
  
// Create LocalDB instance by calling the create API proxy function included by macro  
if (FAILED(hr = LocalDBCreateInstance( L"12.0", L"name", 0)))  
{  
...  
}  
...  
  
```  
  
  
