---
title: "Opération de point de contrôle pour les tables optimisées en mémoire | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47975bd5-373f-43cd-946a-da8e8088b610
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 04176fec3cc190cba1a89a11780d84561512431a
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="checkpoint-operation-for-memory-optimized-tables"></a>Opération de point de contrôle pour les tables mémoire optimisées
  Un point de contrôle doit être effectué régulièrement pour que les données mémoire optimisées dans les fichiers de données/delta puissent anticiper la partie active du journal des transactions. Le point de contrôle permet aux tables mémoire optimisées de restaurer ou récupérer le dernier point de contrôle réussi, puis la partie active du journal des transactions est appliquée pour mettre à jour les tables mémoire optimisées afin de terminer la récupération. Les opérations de point de contrôle des tables sur disque et des tables mémoire optimisées sont des opérations distinctes. La section suivante décrit différents scénarios et le comportement des points de contrôle pour les tables sur disque et les tables mémoire optimisées :  
  
## <a name="manual-checkpoint"></a>Point de contrôle manuel  
 Lorsque vous définissez un point de contrôle manuel, le point de contrôle des tables sur disque et des tables mémoire optimisées est fermé. Le fichier de données actif est fermé même s'il est partiellement rempli.  
  
## <a name="automatic-checkpoint"></a>Point de contrôle automatique  
 Le point de contrôle automatique est implémenté différemment pour les tables sur disque et pour les tables mémoire optimisées en raison des différentes méthodes de persistance des données.  
  
 Pour les tables sur disque, un point de contrôle automatique est pris en fonction de l’option de configuration de l’intervalle de récupération (pour plus d’informations, consultez [Modifier la durée de récupération cible d’une base de données &#40;SQL Server&#41;](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md)).  
  
 Pour les tables à mémoire optimisée, un point de contrôle automatique est pris quand le journal des transactions occupe plus de 1,5 Go depuis le dernier point de contrôle. Cette taille de 1,5 Go comprend les enregistrements du journal des transactions pour les tables sur disque et celles à mémoire optimisée.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et gestion du stockage des objets mémoire optimisés](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  

