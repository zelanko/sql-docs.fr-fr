---
title: Partitions et Mode DirectQuery (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5f179ba9-6efb-46ae-90e5-945bbfddb719
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1fe22de3cc0718647de84345260017a4dd4e477e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66067308"
---
# <a name="partitions-and-directquery-mode-ssas-tabular"></a>Partitions et mode DirectQuery (SSAS Tabulaire)
  Cette section explique comment sont utilisées les partitions dans les modèles DirectQuery. Pour obtenir des informations générales sur les partitions dans les modèles tabulaires, consultez [Partitions &#40;SSAS Tabulaire&#41;](partitions-ssas-tabular.md).  
  
 Pour obtenir des instructions sur la modification de la partition qui est utilisée, ou afficher des informations sur la partition, consultez [modifier la DirectQuery Partition &#40;tabulaire SSAS&#41;](../change-the-directquery-partition-ssas-tabular.md).  
  
## <a name="using-partitions-in-directquery-mode"></a>Utilisation de partitions en mode DirectQuery  
 Pour chaque table, vous devez spécifier une seule partition à utiliser en tant que source de données DirectQuery.  S'il existe plusieurs partitions, lorsque vous basculez le modèle pour activer le mode DirectQuery, par défaut la première partition qui a été créée dans la table est marquée en tant que partition DirectQuery. Vous pouvez modifier ce comportement ultérieurement à l'aide du Gestionnaire de partitions de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Pourquoi autoriser une seule partition en mode DirectQuery ?  
  
 Dans les modèles tabulaires (comme dans les modèles OLAP), les partitions d'une table sont définies par des requêtes SQL. Le développeur qui crée la définition de partition doit s'assurer que les partitions ne se chevauchent pas. Analysis Services ne vérifie pas si les enregistrements appartiennent à une ou plusieurs partitions.  
  
 Les partitions dans un modèle tabulaire mis en cache se comportent de la même manière. Si vous utilisez un modèle en mémoire, lors de l'accès au cache, les formules DAX sont évaluées pour chaque partition et les résultats sont associés. Toutefois, lorsqu'un modèle tabulaire utilise le mode DirectQuery, il est impossible d'évaluer plusieurs partitions, de combiner les résultats et de les convertir en une instruction SQL pour l'envoi à la banque de données relationnelle. Cela peut entraîner une perte inacceptable de performances, ainsi que des inexactitudes potentielles à mesure que les résultats sont agrégés.  
  
 Par conséquent, pour les requêtes ayant obtenu une réponse en mode DirectQuery, le serveur utilise une seule partition qui a été marquée comme partition principale pour l’accès DirectQuery, que l’on appelle *partition DirectQuery*.  La requête SQL spécifiée dans la définition de cette partition définit l’ensemble complet des données qui peuvent être utilisées pour répondre aux requêtes en mode DirectQuery.  
  
 Si vous ne définissez aucune partition de manière explicite, le moteur transmet simplement une requête SQL à l'ensemble de la source de données relationnelle, effectue toutes les opérations reposant sur un jeu dictées par la formule DAX et retourne les résultats de la requête.  
  
 Si vous disposez de plusieurs partitions dans une table et sélectionnez une partition en tant que partition DirectQuery, par défaut, toutes les autres partitions sont marquées comme étant utilisables en mémoire uniquement.  
  
## <a name="partitions-in-cached-models-and-in-directquery-models"></a>Partitions dans les modèles mis en cache et dans les modèles DirectQuery  
 Lorsque vous configurez une partition DirectQuery, vous devez spécifier les options de traitement pour la partition.  
  
 Il existe deux options de traitement pour la partition DirectQuery. Pour définir cette propriété, utilisez le **Gestionnaire de partitions** de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ou [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis sélectionnez la propriété **Option de traitement** . Le tableau suivant répertorie les valeurs de cette propriété, et décrit les effets de chaque valeur lorsqu'elle est associée à la propriété DirectQueryUsage sur la chaîne de connexion :  
  
|**DirectQueryUsage** propriété|Propriété**Option de traitement**|Remarques|  
|-----------------------------------|------------------------------------|-----------|  
|DirectQuery|Ne jamais traiter cette partition|Lorsque le modèle utilise DirectQuery uniquement, le traitement n'est jamais nécessaire.<br /><br /> Dans les modèles hybrides, vous pouvez configurer la partition DirectQuery de façon à ce qu'elle ne soit jamais traitée. Par exemple, si vous effectuez une opération sur un jeu de données très volumineux et vous ne souhaitez pas que les résultats complets soient ajoutés dans le cache, vous pouvez spécifier que la partition DirectQuery inclut l'union des résultats pour toutes les autres partitions dans la table, et ne jamais traiter l'union. Les requêtes transmises à la source relationnelle ne sont pas affectées, et les requêtes sur des données en mémoire cache associent les données des autres partitions.|  
|InMemory avec DirectQuery|Autoriser le traitement de la partition|Si le modèle utilise le mode hybride, vous devez utiliser la même partition pour les requêtes sur InMemory et les requêtes sur la source de données DirectQuery.|  
  
## <a name="see-also"></a>Voir aussi  
 [Partitions &#40;SSAS Tabulaire&#41;](partitions-ssas-tabular.md)  
  
  
