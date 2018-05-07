---
title: Ensemble de lignes DISCOVER_TRANSACTIONS | Documents Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4084d4a964a901c7f4fc78114f596ef9d6708dc3
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="discovertransactions-rowset"></a>DISCOVER_TRANSACTIONS, ensemble de lignes
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Retourne l'ensemble actuel des transactions en attente sur le système.  
  
 **S'applique à :** modèles tabulaires, modèles multidimensionnels  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes **DISCOVER_TRANSACTIONS** contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type| Description|  
|-----------------|--------------------|-----------------|  
|**IDENTIFICATEUR TRANSACTION_ID :**|**DBTYPE_WSTR**|Identificateur unique de la transaction, tel qu'un GUID.|  
|**TRANSACTION_SESSION_ID**|**DBTYPE_WSTR**|Identificateur unique de la session de transaction, tel qu'un GUID.|  
|**TRANSACTION_START_TIME**|**DBTYPE_DBTIMESTAMP**|Date et heure UTC du serveur auxquelles la transaction a démarrée.|  
|**TRANSACTION_ELAPSED_TIME_MS**|**DBTYPE_I8**|Durée écoulée, en millisecondes, depuis le début de l'exécution de la transaction.|  
|**TRANSACTION_CPU_TIME_MS**|**DBTYPE_I8**|Temps processeur, en millisecondes, consommé par toutes les requêtes depuis le début de la transaction.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 L'ensemble de lignes **DISCOVER_TRANSACTIONS** peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|**Nom de colonne**|**Indicateur de type**|**État de la restriction**|  
|---------------------|------------------------|---------------------------|  
|**ID**|**DBTYPE_WSTR**|Ce paramètre est facultatif.|  
|**SESSION_ID**|**DBTYPE_WSTR**|Ce paramètre est facultatif.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilisation d'ADOMD.NET pour retourner l'ensemble de lignes  
 Lorsque vous utilisez ADOMD.NET et l'ensemble de lignes de schéma pour récupérer des métadonnées, vous pouvez utiliser un GUID ou une chaîne pour référencer un objet d'ensemble de lignes de schéma dans la méthode GetSchemaDataSet. Pour plus d'informations, consultez [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Le tableau suivant fournit le GUID et les valeurs de chaîne qui identifient cet ensemble de lignes.  
  
|Argument|Valeur|  
|--------------|-----------|  
|GUID|a07ccd28-8148-11d0-87bb-00c04fc33942|  
|Chaîne|DISCOVER_TRANSACTIONS|  
  
## <a name="see-also"></a>Voir aussi  
 [XML for Analysis ensembles de lignes de schéma](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
