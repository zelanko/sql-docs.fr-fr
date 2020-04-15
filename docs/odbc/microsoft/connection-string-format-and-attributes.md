---
title: Format et attributs de chaîne de connexion Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connection strings [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], connection strings
ms.assetid: 0c360112-8720-4e54-a1a6-b9b18d943557
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d95866976d2e83c058f83b3a0ae5e9a4e8888ed1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81281149"
---
# <a name="connection-string-format-and-attributes"></a>Format et attributs de la chaîne de connexion
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Au lieu d’utiliser une boîte de dialogue, certaines applications peuvent nécessiter une chaîne de connexion qui spécifie les informations de connexion source de données. La chaîne de connexion est composée d’un certain nombre d’attributs qui spécifient comment un pilote se connecte à une source de données. Un attribut identifie un élément d’information spécifique que le conducteur doit connaître avant de pouvoir établir la connexion source de données appropriée. Chaque pilote peut avoir un ensemble différent d’attributs, mais le format de chaîne de connexion est toujours le même. Une chaîne de connexion a le format suivant :  
  
```  
"DSN=data-source-name[;SERVER=value] [;PWD=value] [;UID=value] [;<Attribute>=<value>]"  
```  
  
> [!NOTE]  
>  Le pilote Microsoft ODBC pour Oracle prend en charge le format `CONNECTSTRING`de `SERVER=`chaîne de connexion de la première version du pilote, qui a utilisé au lieu de .  
  
 Si vous vous connectez à un fournisseur de sources `Trusted_Connection=yes` de données qui prend en charge l’authentification de Windows, vous devez spécifier au lieu d’informations d’identification et de mot de passe de l’utilisateur dans la chaîne de connexion.  
  
 Vous devez spécifier le nom source de données si vous ne spécifiez pas les attributs UID, PWD, SERVER (ou CONNECTSTRING) et DRIVER. Cependant, tous les autres attributs sont facultatifs. Si vous ne spécifiez pas un attribut, cet attribut est par défaut à celui spécifié dans l’onglet DSN pertinent de la boîte de dialogue de l’administrateur de source de **données ODBC.** La valeur d’attribut peut être sensible aux cas.  
  
 Les attributs de la chaîne de connexion sont les suivants :  
  
|Attribut|Description|Valeur par défaut|  
|---------------|-----------------|-------------------|  
|DSN|Le nom de source de données figurant dans l’onglet Drivers de la boîte de dialogue **de l’administrateur de source de données ODBC.**|""|  
|PWD|Le mot de passe pour le serveur Oracle que vous souhaitez accéder. Ce pilote prend en charge les limitations qu’Oracle place sur les mots de passe.|""|  
|SERVER|La chaîne de connexion pour le serveur Oracle que vous souhaitez accéder.|""|  
|Identificateur d’utilisateur|Nom d’utilisateur d’Oracle Server. Selon votre système, cet attribut peut ne pas être facultatif - c’est-à-dire que certaines bases de données et tableaux peuvent nécessiter cet attribut à des fins de sécurité.<br /><br /> Utilisez "/" pour utiliser l’authentification du système d’exploitation d’Oracle.|""|  
|BUFFERSIZE|La taille optimale du tampon utilisée lors de l’utilisation des colonnes.<br /><br /> Le pilote optimise l’aller chercher de sorte que l’on se rend sur le serveur Oracle retourne suffisamment de lignes pour remplir un tampon de cette taille. Les valeurs plus grandes ont tendance à augmenter les performances si vous obtenez beaucoup de données.|65535|  
|SYNONYMCOLUMNS|Lorsque cette valeur est vraie (1), un appel SQLColumn( ) API renvoie des informations de colonne. Sinon, SQLColumn) ) ne retourne que des colonnes pour les tables et les vues. Le pilote ODBC pour Oracle offre un accès plus rapide lorsque cette valeur n’est pas définie.|1|  
|Remarques|Lorsque cette valeur est vraie (1), le conducteur retourne des colonnes remarques pour [l’ensemble de résultats SQLColumns.](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md) Le pilote ODBC pour Oracle offre un accès plus rapide lorsque cette valeur n’est pas définie.|0|  
|StdDayOfWeek StdDayOfWeek|Applique la norme ODBC pour le scalar DAYOFWEEK. Par défaut, cela est activé, mais les utilisateurs qui ont besoin de la version localisée peuvent changer le comportement pour utiliser tout ce qu’Oracle retourne.|1|  
|DevinezTheColDef|Précise si le conducteur doit ou non retourner une valeur non nulle pour *l’argument cbColDef* de **SQLDescribeCol**. S’applique uniquement aux colonnes où il n’y a pas d’échelle définie par Oracle, telles que les colonnes numériques calculées et les colonnes définies comme NUMBER sans précision ni échelle. Un appel **SQLDescribeCol** renvoie 130 pour la précision quand Oracle ne fournit pas cette information.|0|  
  
 Par exemple, une chaîne de connexion qui se connecte à la source de données MyDataSource à l’aide du serveur MyOracleServerOracle et de l’utilisateur d’Oracle MyUserID serait :  
  
```  
"DSN={MyDataSource};UID={MyUserID};PWD={MyPassword};SERVER={MyOracleServer}"  
```  
  
 Une chaîne de connexion qui se connecte à la source de données MyOtherDataSource à l’aide de l’authentification du système d’exploitation et du serveur MyOtherOracleServerOracle serait :  
  
```  
"DSN=MyOtherDataSource;UID=/;PWD=;SERVER=MyOtherOracleServer"  
```
