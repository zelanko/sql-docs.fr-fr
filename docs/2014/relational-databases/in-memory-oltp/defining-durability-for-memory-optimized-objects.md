---
title: Définition de la durabilité des objets mémoire optimisés | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 0fe85fbf-8e8d-4983-96fd-d04b3c7d6d65
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: ecf171c8c50e1f7ce1e7cdc9e86cd27ac6fe558b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48169549"
---
# <a name="defining-durability-for-memory-optimized-objects"></a>Définition de la durabilité des objets mémoire optimisés
  L'OLTP en mémoire garantit l'atomicité complète, la cohérence, l'isolation et les propriétés de durabilité complète (ACID). Dans le contexte de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et des tables mémoire optimisées, la durabilité fournit les garanties suivantes :  
  
 Durabilité transactionnelle  
 Lorsque vous validez une transaction à durabilité complète ayant effectué des modifications (DDL ou DML) dans une table mémoire optimisée, les modifications apportées à une table durable mémoire optimisée sont conservées.  
  
 Lorsque vous validez une transaction durable retardée pour une table mémoire optimisée, la transaction devient durable uniquement après que le journal de transactions en mémoire a été enregistré sur le disque.  
  
 Durabilité au redémarrage  
 Lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] redémarre après un incident ou un arrêt programmé, les tables durables mémoire optimisées sont réinstanciées afin d'être restaurées à l'état précédant l'incident ou l'arrêt programmé.  
  
 Durabilité en cas de défaillance du support  
 Si un disque endommagé ou corrompu contient une ou plusieurs copies persistantes d'objets durables mémoire optimisés, la fonctionnalité de sauvegarde et de restauration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restaure les tables mémoire optimisées sur le nouveau support.  
  
 Il existe deux options de durabilité pour les tables mémoire optimisées :  
  
 SCHEMA_ONLY (table non durable)  
 Cette option garantit la durabilité du schéma de la table, y compris les index. Lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est redémarré, la table non durable est recréée, mais démarre sans données (contrairement à une table dans tempdb, où ni la table ni ses données sont conservées au redémarrage). Selon un scénario classique, pour créer une table non durable, il faut stocker les données temporaires, comme une table de mise en lots pour un processus ETL. Avec une durabilité SCHEMA_ONLY, il n'y a pas de journalisation ni de point de contrôle des transactions, ce qui peut considérablement réduire les opérations d'E/S.  
  
 SCHEMA_AND_DATA (table durable)  
 Cette option fournit la durabilité du schéma et des données. Le niveau de durabilité des données varie selon que vous choisissez de valider une transaction avec une durabilité complète ou avec durabilité retardée. Les transactions à durabilité complète offrent la même garantie de durabilité pour le schéma et les données qu'une table sur disque. La durabilité retardée améliore les performances, mais peut entraîner une perte de données en cas d'incident ou de basculement du serveur. (Pour plus d’informations sur la durabilité retardée, consultez [Contrôler la durabilité d’une transaction](../logs/control-transaction-durability.md).)  
  
 Le schéma de la table mémoire optimisée est persistant, comme dans les tables sur disque, dans le groupe de fichiers primaire d'une base de données.  
  
 Les données des tables durables mémoire optimisées sont stockées dans des paires de fichiers de données et de fichiers delta.  
  
 Les index définis dans les tables mémoire optimisées sont persistants uniquement dans les métadonnées, mais pas dans le stockage. Les structures d'index sont générées lors du chargement des tables mémoire optimisées.  
  
 Les lignes sont supprimées explicitement par une instruction DELETE, ou indirectement par une instruction UPDATE. Une opération de mise à jour (UPDATE) équivaut à une suppression suivie d'une insertion. Lorsqu'une ligne est supprimée, aucune modification n'est apportée au fichier de données, mais une nouvelle ligne, identifiant la ligne supprimée, est ajoutée au fichier delta correspondant.  
  
 Lors des opérations de récupération et de restauration, le moteur de l'OLTP en mémoire lit les fichiers delta et de données pour charger les données dans la mémoire physique. Le temps de chargement est déterminé par les facteurs suivants :  
  
-   Quantité de données à charger.  
  
-   Bande passante d'E/S séquentielle.  
  
-   Degré de parallélisme, déterminé par le nombre de conteneurs de fichiers et de noyaux de processeur.  
  
-   Nombre d'enregistrements de journal dans la partie active du journal devant être restaurés par progression.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et gestion du stockage des objets mémoire optimisés](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
