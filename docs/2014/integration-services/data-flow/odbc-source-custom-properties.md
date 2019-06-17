---
title: Propriétés personnalisées des sources ODBC | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 362bbcd8-b7b0-4bab-8afe-1212b2ad1af9
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 9239c1022cd9dfab1edba675c21e69129efe36c1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62770975"
---
# <a name="odbc-source-custom-properties"></a>Propriétés personnalisées des sources ODBC
  Le tableau suivant décrit les propriétés personnalisées de la source ODBC. Toutes les propriétés peuvent être définies à partir des expressions de propriété SSIS.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|Connexion|Connexion ODBC|Connexion ODBC utilisée pour accéder à la base de données source.|  
|AccessMode|Integer (énumération)|Mode utilisé pour accéder à la base de données. Les valeurs possibles sont Nom de la table (0) et Commande SQL (1).<br /><br /> La valeur par défaut est Nom de la table (0).|  
|BatchSize|Entier|Taille du lot pour l'extraction en bloc. Il s'agit du nombre d'enregistrements extraits en tant que table. Si le fournisseur ODBC sélectionné ne prend pas en charge les tables, la taille de lot est 1.|  
|BindCharColumnAs|Integer (énumération)|Cette propriété détermine la manière dont la source ODBC lie les colonnes avec des types chaîne à plusieurs octets, telles que SQL_CHAR, SQL_VARCHAR ou SQL_LONGVARCHAR.<br /><br /> Les valeurs possibles sont Unicode (0), qui lie les colonnes en tant que SQL_C_WCHAR, et ANSI (1), qui lie les colonnes en tant SQL_C_CHAR). La valeur par défaut est Unicode (0).<br /><br /> **Remarque** : cette propriété n’est pas disponible dans **l’Éditeur de source ODBC**, mais elle peut être définie avec **l’Éditeur avancé**.|  
|BindNumericAs|Integer (énumération)|Cette propriété détermine la manière dont la source ODBC lie les colonnes comportant des données numériques avec les types de données SQL_TYPE_NUMERIC et SQL_TYPE_DECIMAL.<br /><br /> Les options possibles sont Char (0), qui lie les colonnes en tant que SQL_C_CHAR et Numérique (1), qui lie les colonnes en tant que SQL_C_NUMERIC. La valeur par défaut est Char (0).<br /><br /> **Remarque** : cette propriété n’est pas disponible dans **l’Éditeur de source ODBC**, mais elle peut être définie avec **l’Éditeur avancé**.|  
|DefaultCodePage|Entier|Page de codes à utiliser pour les colonnes de sortie de chaîne.<br /><br /> **Remarque** : cette propriété n’est pas disponible dans **l’Éditeur de source ODBC**, mais elle peut être définie avec **l’Éditeur avancé**.|  
|ExposeCharColumnsAsUnicode|Booléen|Cette propriété détermine la manière dont le composant expose les colonnes CHAR. La valeur par défaut est False, qui indique que les colonnes CHAR sont exposées en tant que chaînes à plusieurs octets (DT_STR). Si la valeur est True, les colonnes CHAR sont exposées en tant que chaînes étendues (DT_WSTR).<br /><br /> **Remarque** : cette propriété n’est pas disponible dans **l’Éditeur de source ODBC**, mais elle peut être définie avec **l’Éditeur avancé**.|  
|FetchMethod|Integer (énumération)|Méthode utilisée pour obtenir les données. Les options possibles sont Ligne par ligne (0) et Lot (1). La valeur par défaut est Lot (1).<br /><br /> Pour plus d’informations sur ces options, consultez [Source ODBC](odbc-source.md).<br /><br /> **Remarque** : cette propriété n’est pas disponible dans **l’Éditeur de source ODBC**, mais elle peut être définie avec **l’Éditeur avancé**.|  
|SqlCommand|String|Commande SQL à exécuter lorsque la valeur d'AccessMode est Commande SQL.|  
|StatementTimeout|Entier|Nombre de secondes pendant lequel attendre l'exécution d'une instruction SQL avant de la retourner à l'application avec une erreur. La valeur par défaut est 0. La valeur 0 indique que le système n'expire pas.|  
|TableName|String|Nom de la table contenant les données utilisées lorsqu'AccessMode a la valeur Nom de la table.|  
|LobChunckSize|Entier|Taille de segment allouée pour les colonnes LOB.|  
||||  
  
## <a name="see-also"></a>Voir aussi  
 [Source ODBC](odbc-source.md)   
 [Éditeur de source ODBC &#40;page Gestionnaire de connexions&#41;](../odbc-source-editor-connection-manager-page.md)  
  
  
