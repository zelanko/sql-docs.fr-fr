---
title: Attacher et détacher des bases de données Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.ssms.detachdatabase.f1
- sql12.asvs.ssms.attachdatabase.f1
- sql12.asvs.ssmsimbi.AttachDatabase.f1
- sql12.asvs.ssmsimbi.DetachDatabase.f1
helpviewer_keywords:
- databases [Analysis Services], attach
- databases [Analysis Services], detach
ms.assetid: 41887413-2d47-49b8-8614-553cb799fb18
caps.latest.revision: 23
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4e9853b445f795d5bafdfb8839496056a521900d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37271745"
---
# <a name="attach-and-detach-analysis-services-databases"></a>Attacher et détacher des bases de données Analysis Services
  Il existe souvent des cas où un administrateur de base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (dba) souhaite mettre une base de données hors connexion pendant un certain temps, puis la replacer en ligne sur la même (ou une autre) instance de serveur. Ces cas sont souvent motivés par des impératifs d’exploitation, tels que le déplacement de la base de données vers un autre disque afin d’obtenir de meilleures performances, le gain de place afin de permettre la croissance de la base de données, ou la mise à niveau d'un produit. Pour tous ces cas et bien plus encore, le `Attach` et `Detach` commandes activent le [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dba pour mettre la base de données hors connexion et la mettre en ligne avec peu d’efforts.  
  
## <a name="attach-and-detach-commands"></a>Commandes Attach et Detach  
 Le `Attach` commande vous permet de mettre en ligne une base de données qui a été mis hors connexion. Vous pouvez attacher la base de données à l'instance de serveur d'origine ou à une autre instance. Lorsque vous attachez une base de données, l'utilisateur peut spécifier le paramètre **ReadWriteMode** pour la base de données. La commande `Detach` permet de placer en mode hors connexion une base de données du serveur.  
  
## <a name="attach-and-detach-usage"></a>Utilisation des commandes Attach et Detach  
 Le `Attach` commande est utilisée pour mettre en ligne une structure de base de données existante. Si la base de données est attachée en `ReadWrite` mode, il peut être jointe qu’une seule fois à une instance de serveur. Toutefois, si la base de données est attachée en `ReadOnly` mode, il peut être jointe plusieurs fois pour différentes instances de serveur. Par ailleurs, la même base de données ne peut pas être attachée plus d'une fois à la même instance de serveur. Une erreur est déclenchée en cas de tentative faite pour attacher la même base de données plusieurs fois, même si les données ont été copiées dans des dossiers distincts.  
  
> [!IMPORTANT]  
>  S'il a été demandé un mot de passe pour détacher la base de données, le même mot de passe est requis pour attacher la base de données.  
  
 Le `Detach` commande est utilisée pour mettre hors connexion une structure de base de données existante. Lorsqu'une base de données est détachée, vous devez fournir un mot de passe pour protéger les métadonnées confidentielles.  
  
> [!IMPORTANT]  
>  Pour protéger le contenu des fichiers de données, vous devez utiliser une liste de contrôle d'accès pour le dossier, les sous-dossiers et les fichiers de données.  
  
 Lorsque vous détachez une base de données, le serveur suit les étapes ci-après.  
  
|Détachement d'une base de données en lecture/écriture|Détachement d'une base de données en lecture seule|  
|--------------------------------------|-------------------------------------|  
|1) Le serveur émet une demande de verrou CommitExclusive sur la base de données.<br />2) Le serveur attend que toutes les transactions en cours soient validées ou annulées.<br />3) Le serveur génère toutes les métadonnées dont il a besoin pour détacher la base de données.<br />4) La base de données est marquée comme supprimée.<br />5) Le serveur valide la transaction.|1) La base de données est marquée comme supprimée.<br />2) Le serveur valide la transaction.<br /><br /> <br /><br /> Remarque : le mot de passe qui sert à détacher la base de données ne peut pas être modifié pour une base de données en lecture seule. Une erreur est déclenchée si un paramètre de mot de passe est fourni pour une base de données attachée contenant déjà un mot de passe.|  
  
 Les commandes `Attach` et `Detach` doivent être exécutées comme de simples opérations. Elles ne peuvent pas être combinées à d'autres opérations de la même transaction. En outre, le `Attach` et `Detach` commandes sont des commandes transactionnelles atomiques. Cela signifie que soit l'opération réussit, soit elle échoue. Aucune base de données ne demeurera dans un état inachevé.  
  
> [!IMPORTANT]  
>  Serveur ou des privilèges d’administrateur de base de données sont nécessaires pour exécuter le `Detach` commande.  
  
> [!IMPORTANT]  
>  Les privilèges d'administrateur de serveur sont requis pour exécuter la commande `Attach`.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Déplacer une base de données Analysis Services](move-an-analysis-services-database.md)   
 [Base de données ReadWriteModes](database-readwritemodes.md)   
 [Basculer une base de données Analysis Services entre les modes ReadOnly et ReadWrite](switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)   
 [Élément Detach](../xmla/xml-elements-commands/detach-element.md)   
 [Attach, élément](../xmla/xml-elements-commands/attach-element.md)  
  
  
