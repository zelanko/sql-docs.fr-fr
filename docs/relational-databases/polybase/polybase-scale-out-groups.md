---
title: Groupes de scale-out PolyBase | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
helpviewer_keywords:
- PolyBase
- PolyBase, scale-out groups
- scale-out PolyBase
ms.assetid: c7810135-4d63-4161-93ab-0e75e9d10ab5
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 53802a8a327c2e66810cd8f084d0ba297eb95426
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47629937"
---
# <a name="polybase-scale-out-groups"></a>Groupes de scale-out PolyBase

[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Une instance de SQL Server autonome avec PolyBase peut se transformer en goulot d’étranglement de performances lors du traitement de gros volumes de jeux données dans Hadoop ou le stockage d’objets Blob Azure. La fonctionnalité Groupe PolyBase vous permet de créer un cluster d’instances SQL Server pour traiter de grands volumes de jeux de données à partir de sources de données externes telles que Hadoop ou le stockage Blob Azure en utilisant une opération de scale-out pour de meilleures performances de requête. Vous pouvez maintenant adapter votre calcul SQL Server pour répondre aux besoins de performances de votre charge de travail. Les groupes de scale-out PolyBase, groupe d’instances SQL Server, vous permettent de traiter de grands jeux de données externes dans une architecture de traitement parallèle. Les performances de chargement de données et de requête peuvent augmenter de façon linéaire quand vous ajoutez d’autres instances SQL Server au groupe. 
  
Consultez [Prise en main de PolyBase](../../relational-databases/polybase/get-started-with-polybase.md) et [Guide de PolyBase](../../relational-databases/polybase/polybase-guide.md).
  
![Groupes de scale-out PolyBase](../../relational-databases/polybase/media/polybase-scale-out-groups.png "Groupes de scale-out PolyBase")  
  
## <a name="head-node"></a>Nœud principal  

Le nœud principal contient l’instance de SQL Server à laquelle les requêtes PolyBase sont envoyées. Chaque groupe PolyBase ne peut avoir qu’un seul nœud principal. Un nœud principal est un regroupement logique du moteur de base de données SQL, du moteur PolyBase et du PolyBase Data Movement Service sur l’instance de SQL Server.
  
## <a name="compute-node"></a>Nœud de calcul  

Un nœud de calcul contient l’instance de SQL Server qui assiste dans le traitement des requêtes avec montée en puissance sur des données externes. Un nœud de calcul est un regroupement logique de SQL Server et du PolyBase Data Movement Service sur l’instance de SQL Server. Un groupe PolyBase peut avoir plusieurs nœuds de calcul. Le nœud principal et les nœuds de calcul doivent tous exécuter la même version de SQL Server.

## <a name="scale-out-reads"></a>Lectures scale-out

Quand des instances SQL Server, Oracle ou Teradata externes sont interrogées, les tables partitionnées bénéficient de lectures scale-out. Chaque nœud d’un groupe de scale-out PolyBase peut faire tourner jusqu’à 8 lecteurs pour lire les données externes. Et chaque lecteur se voit assigner une seule partition à lire dans la table externe. 

Par exemple, supposons que vous avez une table SQL Server externe avec 12 partitions mensuelles et un groupe de scale-out PolyBase à 3 nœuds, chaque nœud utilise 4 lecteurs PolyBase pour traiter chacune des 12 partitions. En voici une illustration dans l’image suivante. 

> [!NOTE]
 C’est différent des lectures scale-out sur Hadoop. 

![Groupes de scale-out PolyBase](../../relational-databases/polybase/media/polybase-scale-out-groups2.png "Groupes de scale-out PolyBase")
  
## <a name="distributed-query-processing"></a>Traitement de requêtes distribuées  

Les requêtes PolyBase sont soumises à SQL Server sur le nœud principal. La partie de la requête qui fait référence à des tables externes est transmise au moteur PolyBase.
  
Le moteur PolyBase est le composant clé des requêtes PolyBase. Il analyse l’interrogation de données externes, génère le plan de requête et distribue le travail au service de déplacement des données sur les nœuds de calcul en vue de l’exécution. Une fois l’exécution terminée, il reçoit les résultats depuis les nœuds de calcul et les soumet à SQL Server en vue de leur traitement et de leur renvoi au client.
  
Le service de déplacement de données PolyBase reçoit des instructions du moteur PolyBase et transfère les données entre HDFS et SQL Server et entre les instances SQL Server sur les nœuds principal et de calcul.
  
## <a name="editions-availability"></a>Disponibilité des éditions  

Après l’installation de SQL Server, l’instance peut être désignée comme un nœud principal ou comme nœud de calcul. Le choix dépend de la version de SQL Server sur laquelle PolyBase est exécuté. Dans une édition Enterprise, l’instance peut être désignée comme nœud principal ou comme nœud de calcul. Dans une édition Standard, l’instance peut uniquement être désignée comme nœud de calcul.

## <a name="next-steps"></a>Étapes suivantes

Pour configurer un groupe de scale-out PolyBase, consultez le guide suivant :

[Améliorer les groupes de scale-out PolyBase sur Windows](configure-scale-out-groups-windows.md)
