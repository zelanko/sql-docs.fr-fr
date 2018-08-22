---
title: Groupe de fichiers à mémoire optimisée | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 14106cc9-816b-493a-bcb9-fe66a1cd4630
caps.latest.revision: 12
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 021bab292e56b9ead1164cd3933efa6c02eb7ee4
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40395108"
---
# <a name="the-memory-optimized-filegroup"></a>Groupe de fichiers mémoire optimisé
  Pour créer des tables mémoire optimisées, vous devez d'abord créer un groupe de fichiers mémoire optimisé. Le groupe de fichiers mémoire optimisé contient un ou plusieurs conteneurs. Chaque conteneur contient des fichiers de données, des fichiers delta ou les deux.  
  
 Bien que les lignes de données dans les tables SCHEMA_ONLY ne soient pas conservées et que les métadonnées des tables mémoire optimisées et des procédures stockées compilées en mode natif soient stockées dans des catalogues traditionnels, le moteur [!INCLUDE[hek_2](../../includes/hek-2-md.md)] requiert toujours un groupe de fichiers mémoire optimisé pour les tables mémoire optimisées SCHEMA_ONLY afin de fournir une expérience uniforme pour les bases de données avec des tables mémoire optimisées.  
  
 Le groupe de fichiers mémoire optimisé est basé sur le groupe de fichiers de flux de fichier, avec les différences suivantes :  
  
-   Vous ne pouvez créer qu'un seul groupe de fichiers mémoire optimisé par base de données. Vous devez marquer explicitement le groupe de fichiers comme contenant memory_optimized_data. Vous pouvez créer le groupe de fichiers lorsque vous créez la base de données, ou vous pouvez l' ajouter ultérieurement :  
  
    ```  
    ALTER DATABASE imoltp ADD FILEGROUP imoltp_mod CONTAINS MEMORY_OPTIMIZED_DATA  
    ```  
  
-   Vous devez ajouter un ou plusieurs conteneurs au groupe de fichiers MEMORY_OPTIMIZED_DATA. Exemple :  
  
    ```  
    ALTER DATABASE imoltp ADD FILE (name='imoltp_mod1', filename='c:\data\imoltp_mod1') TO FILEGROUP imoltp_mod  
    ```  
  
-   Vous n’avez pas besoin d’activer le flux de fichier ([Activer et configurer FILESTREAM](../blob/enable-and-configure-filestream.md)) pour créer un groupe de fichiers mémoire optimisé. Le mappage au flux de fichier est effectué par le moteur [!INCLUDE[hek_2](../../includes/hek-2-md.md)] .  
  
-   Vous pouvez ajouter de nouveaux conteneurs à un groupe de fichiers mémoire optimisé. Vous pouvez avoir besoin d'un nouveau conteneur pour développer le stockage requis pour la table durable, mémoire optimisée, et également pour répartir les E/S sur plusieurs conteneurs.  
  
-   Le déplacement des données avec un groupe de fichiers mémoire optimisé est optimisé dans une configuration de groupe de disponibilité AlwaysOn. Contrairement aux fichiers de flux de fichier envoyés aux réplicas secondaires, les fichiers de point de contrôle (de données et delta) du groupe de fichiers mémoire optimisé ne sont pas envoyés aux réplicas secondaires. Les fichiers de données et delta sont construits à l'aide du journal des transactions sur le réplica secondaire.  
  
 Limitations suivantes du groupe de fichiers mémoire optimisé,  
  
-   Une fois que vous avez créé un groupe de fichiers mémoire optimisé, vous ne pouvez le supprimer qu'en supprimant la base de données. Dans un environnement de production, il est peu probable que vous deviez supprimer le groupe de fichiers mémoire optimisé.  
  
-   Vous ne pouvez pas supprimer un conteneur non vide ni déplacer des paires de fichiers de données et delta vers un autre conteneur dans le groupe de fichiers mémoire optimisé.  
  
-   Vous ne pouvez pas spécifier MAXSIZE pour le conteneur.  
  
## <a name="configuring-a-memory-optimized-filegroup"></a>Configuration d'un groupe de fichiers mémoire optimisé  
 Vous devez envisager de créer plusieurs conteneurs dans le groupe de fichiers mémoire optimisé et de les répartir sur différents lecteurs afin d'obtenir davantage de bande passante pour transmettre en continu les données en mémoire.  
  
 Lors de la configuration du stockage, vous devez fournir un espace libre correspondant à quatre fois la taille des tables mémoire optimisées durables. Vous devez également garantir que le sous-système d'E/S prend en charge les IOPS requises pour votre charge de travail. Si les paires de fichiers de données et delta sont définies à un niveau d'IOPS donné, vous avez besoin de 3 fois cette valeur d'IOPS pour tenir compte des opérations de stockage et de fusion. Vous pouvez ajouter une capacité de stockage et des IOPS en ajoutant un ou plusieurs conteneurs au groupe de fichiers mémoire optimisé.  
  
 Dans un scénario à plusieurs conteneurs et à plusieurs lecteurs, les fichiers de données et delta sont alloués dans des conteneurs selon le principe du tourniquet. Le premier fichier de données est alloué depuis le premier conteneur, le fichier delta depuis le conteneur suivant, et ainsi de suite. Cette méthode d'allocation répartit les fichiers de données et delta de manière uniforme entre les conteneurs si vous avez un nombre impair de lecteurs, chacun étant mappé à un conteneur. Toutefois, si vous avez un nombre pair de lecteurs, chacun étant mappé à un conteneur, cela peut entraîner un stockage déséquilibré, les fichiers de données étant mappés aux lecteurs impairs et les fichiers delta aux lecteurs pairs. Pour obtenir un flux équilibré d'E/S lors de la récupération, envisagez de placer des paires de fichiers de données et delta sur les mêmes axes/stockages, comme indiqué dans l'exemple ci-dessous.  
  
 **Exemple :** envisager un groupe de fichiers mémoire optimisé avec deux conteneurs : conteneur 1 sur le lecteur X et conteneur 2 sur le lecteur Y. Dans la mesure où l’allocation des fichiers de données et delta s’effectue de manière alternée, conteneur 1 aura uniquement les fichiers de données et conteneur 2 aura uniquement les fichiers delta, ce qui entraîne une persistance déséquilibrée pour le stockage, ainsi que des opérations d’entrée/sortie par seconde, en tant que fichiers de données sont beaucoup plus volumineuses que les fichiers delta. Pour distribuer les fichiers de données et delta uniformément sur les lecteurs X et Y, créez quatre conteneurs au lieu de deux et mappez les deux premiers conteneurs au lecteur X et les deux conteneurs suivants au lecteur Y. Avec l’allocation de tourniquet (round-robin), les premières données premier fichier delta seront alloués depuis le conteneur-1 et 2 de conteneur respectivement mappés au lecteur X. De même, le fichier suivant de données et delta est alloué depuis le conteneur-3 et 4 conteneur qui sont mappés au lecteur Y. Cela permet de répartir uniformément des fichiers de données et delta entre deux lecteurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et gestion du stockage des objets mémoire optimisés](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
