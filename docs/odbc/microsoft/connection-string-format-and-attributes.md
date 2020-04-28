---
title: Attributs et format de la chaîne de connexion | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81281149"
---
# <a name="connection-string-format-and-attributes"></a>Format et attributs de la chaîne de connexion
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Au lieu d’utiliser une boîte de dialogue, certaines applications peuvent nécessiter une chaîne de connexion qui spécifie les informations de connexion à la source de données. La chaîne de connexion est constituée d’un certain nombre d’attributs qui spécifient la façon dont un pilote se connecte à une source de données. Un attribut identifie une information spécifique que le pilote doit connaître avant de pouvoir établir la connexion à la source de données appropriée. Chaque pilote peut avoir un ensemble différent d’attributs, mais le format de la chaîne de connexion est toujours le même. Une chaîne de connexion a le format suivant :  
  
```  
"DSN=data-source-name[;SERVER=value] [;PWD=value] [;UID=value] [;<Attribute>=<value>]"  
```  
  
> [!NOTE]  
>  Le pilote Microsoft ODBC pour Oracle prend en charge le format de chaîne de connexion de la première version du pilote `CONNECTSTRING`, qui utilisait = au lieu de `SERVER=`.  
  
 Si vous vous connectez à un fournisseur de sources de données qui prend en charge l’authentification `Trusted_Connection=yes` Windows, vous devez spécifier à la place de l’ID d’utilisateur et des informations de mot de passe dans la chaîne de connexion.  
  
 Vous devez spécifier le nom de la source de données si vous ne spécifiez pas les attributs UID, PWD, SERVER (ou CONNECTSTRING) et DRIVER. Toutefois, tous les autres attributs sont facultatifs. Si vous ne spécifiez pas d’attribut, cet attribut est défini par défaut sur celui spécifié sous l’onglet DSN correspondant de la boîte de dialogue **administrateur de sources de données ODBC** . La valeur de l’attribut peut être sensible à la casse.  
  
 Les attributs de la chaîne de connexion sont les suivants :  
  
|Attribut|Description|Valeur par défaut|  
|---------------|-----------------|-------------------|  
|DSN|Nom de la source de données figurant dans l’onglet pilotes de la boîte de dialogue **administrateur de sources de données ODBC** .|""|  
|PWD|Mot de passe du serveur Oracle auquel vous souhaitez accéder. Ce pilote prend en charge les limitations que Oracle place sur les mots de passe.|""|  
|SERVER|Chaîne de connexion pour le serveur Oracle auquel vous souhaitez accéder.|""|  
|Identificateur d’utilisateur|Nom d’utilisateur du serveur Oracle. Selon votre système, cet attribut peut ne pas être facultatif. autrement dit, certaines bases de données et tables peuvent nécessiter cet attribut à des fins de sécurité.<br /><br /> Utilisez « / » pour utiliser l’authentification du système d’exploitation Oracle.|""|  
|TAMPON|Taille de mémoire tampon optimale utilisée lors de l’extraction de colonnes.<br /><br /> Le pilote optimise l’extraction afin qu’une extraction à partir du serveur Oracle retourne suffisamment de lignes pour remplir une mémoire tampon de cette taille. Des valeurs plus élevées tendent à augmenter les performances si vous récupérez un grand nombre de données.|65535|  
|SYNONYMCOLUMNS|Lorsque cette valeur est true (1), un appel d’API SQLColumn () retourne des informations sur les colonnes. Sinon, SQLColumn () retourne uniquement les colonnes des tables et des vues. Le pilote ODBC pour Oracle fournit un accès plus rapide lorsque cette valeur n’est pas définie.|1|  
|Remarques|Lorsque cette valeur est true (1), le pilote retourne les colonnes de remarques pour le jeu de résultats [SQLColumns](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md) . Le pilote ODBC pour Oracle fournit un accès plus rapide lorsque cette valeur n’est pas définie.|0|  
|StdDayOfWeek|Applique la norme ODBC pour la scalaire DAYOFWEEK. Par défaut, cette option est activée, mais les utilisateurs qui ont besoin de la version localisée peuvent modifier le comportement afin d’utiliser n’importe quel retour d’Oracle.|1|  
|GuessTheColDef|Spécifie si le pilote doit retourner une valeur différente de zéro pour l’argument *cbColDef* de **SQLDescribeCol**. S’applique uniquement aux colonnes pour lesquelles il n’existe aucune échelle définie par Oracle, telle que les colonnes numériques calculées et les colonnes définies comme nombre sans précision ou échelle. Un appel de **SQLDescribeCol** retourne 130 pour la précision quand Oracle ne fournit pas ces informations.|0|  
  
 Par exemple, une chaîne de connexion qui se connecte à la source de données MyDataSource à l’aide du serveur MyOracleServerOracle et de l’utilisateur Oracle MyUserID serait la suivante :  
  
```  
"DSN={MyDataSource};UID={MyUserID};PWD={MyPassword};SERVER={MyOracleServer}"  
```  
  
 Une chaîne de connexion qui se connecte à la source de données MyOtherDataSource à l’aide de l’authentification du système d’exploitation et du serveur MyOtherOracleServerOracle serait la suivante :  
  
```  
"DSN=MyOtherDataSource;UID=/;PWD=;SERVER=MyOtherOracleServer"  
```
