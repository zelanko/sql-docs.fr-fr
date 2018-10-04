---
title: Ensemble de lignes DISCOVER_DB_CONNECTIONS | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- DISCOVER_DB_CONNECTIONS rowset
ms.assetid: 12a51a4e-5f3d-4449-9d94-7836fea1bc8b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 51eab7a38da893f0249a64299c08b9a409a4b9a2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48163989"
---
# <a name="discoverdbconnections-rowset"></a>Ensemble de lignes DISCOVER_DB_CONNECTIONS
  Fournit des informations sur l'activité et l'utilisation des ressources des connexions actuellement ouvertes du serveur à une base de données.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DISCOVER_DB_CONNECTIONS` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CONNECTION_CATALOG_NAME`|`DBTYPE_WSTR`||Nom de la base de données actuellement connectée.|  
|`CONNECTION_ID`|`DBTYPE_I4`||Numéro unique qui identifie la connexion.|  
|`CONNECTION_IDLE_TIME_MS`|`DBTYPE_I8`||Durée d'inactivité, en millisecondes, depuis l'établissement de la connexion.|  
|`CONNECTION_IN_USE`|`DBTYPE_I4`||indique si la connexion est active (1) ou inactive (0).|  
|`CONNECTION_LAST_COMMAND_END_TIME`|`DBTYPE_DBTIMESTAMP`||Date et heure UTC du serveur auxquelles l'exécution de la dernière commande s'est achevée.|  
|`CONNECTION_LAST_COMMAND_START_TIME`|`DBTYPE_DBTIMESTAMP`||Date et heure UTC du serveur auxquelles l'exécution de la dernière commande a débuté.|  
|`CONNECTION_SERVER_NAME`|`DBTYPE_WSTR`||Nom du serveur actuellement connecté.|  
|`CONNECTION_SPID`|`DBTYPE_I4`||ID de session.|  
|`CONNECTION_START_TIME`|`DBTYPE_DBTIMESTAMP`||Date et heure UTC du serveur auxquelles la connexion a été établie.|  
|`CONNECTION_USAGE_TIME_MS`|`DBTYPE_I8`||Durée de connexion active, en millisecondes, depuis l'établissement de la connexion.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
> [!IMPORTANT]  
>  L'ensemble de lignes `DISCOVER_DB_CONNECTIONS` affiche des informations uniquement lorsque le service est connecté aux sources de données relationnelles.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `DISCOVER_DB_CONNECTIONS` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|CONNECTION_ID|DBTYPE_I4|Facultatif.|  
|CONNECTION_IN_USE|DBTYPE_I4|Facultatif.|  
|CONNECTION_SERVER_NAME|DBTYPE_WSTR|Facultatif.|  
|CONNECTION_CATALOG_NAME|DBTYPE_WSTR|Obligatoire.|  
|CONNECTION_SPID|DBTYPE_I4|Facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma XML for Analysis](xml-for-analysis-schema-rowsets.md)  
  
  
