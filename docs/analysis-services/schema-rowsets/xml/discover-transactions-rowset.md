---
title: Ensemble de lignes DISCOVER_TRANSACTIONS | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 85789177-c5df-4336-a90c-c20d69277ab4
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7ca0b129013f5bdced79d8fb8245893a3db7ff06
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="discovertransactions-rowset"></a>DISCOVER_TRANSACTIONS, ensemble de lignes
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
Retourne l'ensemble actuel des transactions en attente sur le système.  
  
 **S'applique à :** modèles tabulaires, modèles multidimensionnels  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes **DISCOVER_TRANSACTIONS** contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type| Description|  
|-----------------|--------------------|-----------------|  
|**TRANSACTION_ID**|**DBTYPE_WSTR**|Identificateur unique de la transaction, tel qu'un GUID.|  
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
  
  
