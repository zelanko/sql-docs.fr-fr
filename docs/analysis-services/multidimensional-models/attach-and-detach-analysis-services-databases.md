---
title: "Attacher et détacher des bases de données Analysis Services | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.ssmsimbi.AttachDatabase.f1
- sql13.asvs.ssms.attachdatabase.f1
- sql13.asvs.ssmsimbi.DetachDatabase.f1
- sql13.asvs.ssms.detachdatabase.f1
helpviewer_keywords:
- databases [Analysis Services], attach
- databases [Analysis Services], detach
ms.assetid: 41887413-2d47-49b8-8614-553cb799fb18
caps.latest.revision: "24"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f7cc88be76e8ad64d81465543ab4f463c98687e7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="attach-and-detach-analysis-services-databases"></a>Attacher et détacher des bases de données Analysis Services
  Il existe souvent des cas où un administrateur de base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (dba) souhaite mettre une base de données hors connexion pendant un certain temps, puis la replacer en ligne sur la même (ou une autre) instance de serveur. Ces cas sont souvent motivés par des impératifs d’exploitation, tels que le déplacement de la base de données vers un autre disque afin d’obtenir de meilleures performances, le gain de place afin de permettre la croissance de la base de données, ou la mise à niveau d'un produit. Pour tous ces cas et d’autres, les commandes **Attach** et **Detach** permettent à l’administrateur de base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de placer la base de données hors connexion et de la remettre en ligne de manière simple.  
  
## <a name="attach-and-detach-commands"></a>Commandes Attach et Detach  
 La commande **Attach** permet de mettre en ligne une base de données placée en mode hors connexion. Vous pouvez attacher la base de données à l'instance de serveur d'origine ou à une autre instance. Lorsque vous attachez une base de données, l'utilisateur peut spécifier le paramètre **ReadWriteMode** pour la base de données. La commande **Detach** permet de placer en mode hors connexion une base de données du serveur.  
  
## <a name="attach-and-detach-usage"></a>Utilisation des commandes Attach et Detach  
 La commande **Attach** est utilisée pour mettre en ligne une structure de base de données existante. Si la base de données est attachée en mode **ReadWrite** , elle ne peut être jointe qu'une seule fois à une instance de serveur. Toutefois, si la base de données est attachée en mode **ReadOnly** , elle peut être jointe plusieurs fois aux différentes instances de serveur. Par ailleurs, la même base de données ne peut pas être attachée plus d'une fois à la même instance de serveur. Une erreur est déclenchée en cas de tentative faite pour attacher la même base de données plusieurs fois, même si les données ont été copiées dans des dossiers distincts.  
  
> [!IMPORTANT]  
>  S'il a été demandé un mot de passe pour détacher la base de données, le même mot de passe est requis pour attacher la base de données.  
  
 La commande **Detach** est utilisée pour mettre hors connexion une structure de base de données existante. Lorsqu'une base de données est détachée, vous devez fournir un mot de passe pour protéger les métadonnées confidentielles.  
  
> [!IMPORTANT]  
>  Pour protéger le contenu des fichiers de données, vous devez utiliser une liste de contrôle d'accès pour le dossier, les sous-dossiers et les fichiers de données.  
  
 Lorsque vous détachez une base de données, le serveur suit les étapes ci-après.  
  
|Détachement d'une base de données en lecture/écriture|Détachement d'une base de données en lecture seule|  
|--------------------------------------|-------------------------------------|  
|1) Le serveur émet une demande de verrou CommitExclusive sur la base de données.<br /><br /> 2) Le serveur attend que toutes les transactions en cours soient validées ou annulées.<br /><br /> 3) Le serveur génère toutes les métadonnées dont il a besoin pour détacher la base de données.<br /><br /> 4) La base de données est marquée comme supprimée.<br /><br /> 5) Le serveur valide la transaction.|1) La base de données est marquée comme supprimée.<br /><br /> 2) Le serveur valide la transaction.<br /><br /> Remarque : le mot de passe qui sert à détacher la base de données ne peut pas être modifié pour une base de données en lecture seule. Une erreur est déclenchée si un paramètre de mot de passe est fourni pour une base de données attachée contenant déjà un mot de passe.|  
  
 Les commandes **Attach** et **Detach** doivent être exécutées comme de simples opérations. Elles ne peuvent pas être combinées à d'autres opérations de la même transaction. De même, les commandes **Attach** et **Detach** sont des commandes transactionnelles atomiques. Cela signifie que soit l'opération réussit, soit elle échoue. Aucune base de données ne demeurera dans un état inachevé.  
  
> [!IMPORTANT]  
>  Les privilèges administrateur de serveur ou de base de données sont nécessaires pour exécuter la commande **Detach** .  
  
> [!IMPORTANT]  
>  Les privilèges d’administrateur de serveur sont nécessaires pour exécuter la commande **Attach** .  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Déplacer une base de données Analysis Services](../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)   
 [Base de données ReadWriteModes](../../analysis-services/multidimensional-models/database-readwritemodes.md)   
 [Basculer une base de données Analysis Services entre les modes ReadOnly et ReadWrite](../../analysis-services/multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)   
 [Élément Detach](../../analysis-services/xmla/xml-elements-commands/detach-element.md)   
 [Attach, élément](../../analysis-services/xmla/xml-elements-commands/attach-element.md)  
  
  
