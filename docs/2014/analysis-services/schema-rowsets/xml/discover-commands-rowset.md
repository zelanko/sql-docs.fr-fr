---
title: Ensemble de lignes DISCOVER_COMMANDS | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- DISCOVER_COMMANDS rowset
ms.assetid: d228f265-05d9-4d2c-a622-44c73eab7a71
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 14c4eb9ac8fe63422ee29f5880a8a5f1eb6329bf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045252"
---
# <a name="discovercommands-rowset"></a>Ensemble de lignes DISCOVER_COMMANDS
  Fournit des informations sur l'activité et l'utilisation des ressources des dernières commandes exécutées ou des commandes en cours d'exécution sur les connexions ouvertes sur le serveur.  
  
 **S'applique à :** modèles tabulaires, modèles multidimensionnels  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DISCOVER_COMMANDS` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Restriction|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|`SESSION_SPID`|`DBTYPE_I4`|Oui|ID de session.|  
|`SESSION_COMMAND_COUNT`|`DBTYPE_I4`||Nombre de commandes exécutées depuis le début de la session.|  
|`COMMAND_START_TIME`|`DBTYPE_DBTIMESTAMP`||Date et heure de démarrage de la dernière commande, exprimées en heure UTC sur le serveur.|  
|`COMMAND_ELAPSED_TIME_MS`|`DBTYPE_I8`||Durée écoulée, en millisecondes, depuis le début de l'exécution de la commande.|  
|`COMMAND_CPU_TIME_MS`|`DBTYPE_I8`||Temps processeur, en millisecondes, utilisé par la commande depuis le début de son exécution.|  
|`COMMAND_READS`|`DBTYPE_I8`||Nombre cumulé de lectures sur le disque depuis le début de l'exécution de la commande.|  
|`COMMAND_READ_KB`|`DBTYPE_I8`||Valeur cumulée des données lues à partir du disque, en kilo-octets, depuis le début de l'exécution de la commande.|  
|`COMMAND_WRITES`|`DBTYPE_I8`||Nombre cumulé d'écritures sur le disque depuis le début de l'exécution de la commande.|  
|`COMMAND_WRITE_KB`|`DBTYPE_I8`||Valeur cumulée des données écrites sur le disque, en kilo-octets, depuis le début de l'exécution de la commande.|  
|`COMMAND_TEXT`|`DBTYPE_WSTR`||Texte de la commande.|  
|`COMMAND_END_TIME`|`DBTYPE_DBTIMESTAMP`||Date et heure UTC du serveur auxquelles l'exécution de la commande s'est achevée.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilisation d'ADOMD.NET pour retourner l'ensemble de lignes  
 Lorsque vous utilisez ADOMD.NET et l'ensemble de lignes de schéma pour récupérer des métadonnées, vous pouvez utiliser un GUID ou une chaîne pour référencer un objet d'ensemble de lignes de schéma dans la méthode GetSchemaDataSet. Pour plus d'informations, consultez [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Le tableau suivant fournit le GUID et les valeurs de chaîne qui identifient cet ensemble de lignes.  
  
|Argument|Valeur|  
|--------------|-----------|  
|GUID|a07ccd34-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|Commandes|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma XML for Analysis](xml-for-analysis-schema-rowsets.md)  
  
  