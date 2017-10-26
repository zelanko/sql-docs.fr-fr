---
title: "Comparaison du stockage des tables sur disque et du stockage des tables optimisées en mémoire | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eacf443c-001a-445f-ad1c-5f5a45eca6f4
caps.latest.revision: 5
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e1d68c71f727aefd0a95bb1e1c95d0a3fe77edb5
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="comparing-disk-based-table-storage-to-memory-optimized-table-storage"></a>Comparaison du stockage des tables sur disque et du stockage des tables optimisées en mémoire
  
  
|Catégories|Table sur disque|Table optimisée en mémoire durable|  
|----------------|-----------------------|-------------------------------------|  
|DDL|Les informations de métadonnées sont stockées dans les tables système dans le groupe de fichiers primaire de la base de données, et sont accessibles via les affichages catalogue.|Les informations de métadonnées sont stockées dans les tables système dans le groupe de fichiers primaire de la base de données, et sont accessibles via les affichages catalogue.|  
|Structure|Les lignes sont stockées dans des pages de 8 Ko. Une page stocke uniquement les lignes de la même table.|Les lignes sont stockées en tant que lignes individuelles. Il n'y a aucune structure de page. Deux lignes consécutives dans un fichier de données peuvent appartenir à des tables optimisées en mémoire différentes.|  
|Index|Les index sont stockés dans une structure de page semblable aux lignes de données.|Seule la définition d'index est conservée (pas les lignes d'index). Les index sont conservés en mémoire et sont régénérés lorsque la table optimisée en mémoire est chargée lors du redémarrage d'une base de données. Étant donné que les lignes d'index ne sont pas conservées, aucune journalisation n'a lieu pour les modifications d'index.|  
|Opération DML|La première étape est la recherche de la page, puis son chargement dans le pool de mémoires tampons.<br /><br /> Insert<br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] insère la ligne dans la page selon le classement des lignes s'il s'agit d'un index cluster.<br /><br /> Supprimer<br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recherche la ligne à supprimer dans la page et la marque comme supprimée.<br /><br /> Update<br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recherche la ligne dans la page. La mise à jour est effectuée sur place pour les colonnes non-clés. La mise à jour de la colonne clé est effectuée par une opération de suppression et d'insertion.<br /><br /> Une fois l'opération DML terminée, les pages concernées sont vidées sur le disque dans le cadre de la stratégie du pool de mémoires tampons, du point de contrôle ou de la validation des transactions pour les opérations avec une journalisation minime. Les opérations de lecture/écriture sur les pages entraînent des E/S superflues.|Pour les tables optimisées en mémoire, les opérations DML sont effectuées directement en mémoire puisque les données résident dans la mémoire. Un thread d'arrière-plan lit les enregistrements du journal des tables optimisées en mémoire et les rend persistants dans les fichiers de données et delta. Une mise à jour génère une nouvelle version de ligne. Mais une mise à jour est journalisée comme une suppression suivie d'une insertion.|  
|Fragmentation des données|La manipulation des données fragmente les données et aboutit à des pages partiellement remplies et à des pages logiquement consécutives qui ne sont pas contiguës sur le disque. Ceci dégrade les performances d'accès aux données et vous oblige à défragmenter des données.|Les données optimisées en mémoire ne sont pas stockées dans des pages, par conséquent, il n'y a pas de fragmentation de données. Toutefois, à mesure que des lignes sont mises à jour/supprimées, les fichiers de données et delta doivent être compactés. Cette opération est effectuée par un thread d'arrière-plan MERGE basé sur une stratégie de fusion.|  
  
## <a name="see-also"></a>Voir aussi  
 [Création et gestion du stockage des objets optimisés en mémoire](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  

