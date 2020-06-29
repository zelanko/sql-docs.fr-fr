---
title: Attacher et détacher des bases de données Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
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
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44698c89eff608d6c993c3cec030098883eb5aee
ms.sourcegitcommit: 04ba0ed3d860db038078609d6e348b0650739f55
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85469004"
---
# <a name="attach-and-detach-analysis-services-databases"></a>Attacher et détacher des bases de données Analysis Services
  Il existe souvent des cas où un administrateur de base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (dba) souhaite mettre une base de données hors connexion pendant un certain temps, puis la replacer en ligne sur la même (ou une autre) instance de serveur. Ces cas sont souvent motivés par des impératifs d’exploitation, tels que le déplacement de la base de données vers un autre disque afin d’obtenir de meilleures performances, le gain de place afin de permettre la croissance de la base de données, ou la mise à niveau d'un produit. Pour tous ces cas, et bien plus encore, les `Attach` `Detach` commandes et permettent [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à l’administrateur de base de données de mettre la base de données hors connexion et de la remettre en ligne avec un minimum d’effort.  
  
## <a name="attach-and-detach-commands"></a>Commandes Attach et Detach  
 La commande `Attach` permet de mettre en ligne une base de données placée en mode hors connexion. Vous pouvez attacher la base de données à l'instance de serveur d'origine ou à une autre instance. Lorsque vous attachez une base de données, l'utilisateur peut spécifier le paramètre **ReadWriteMode** pour la base de données. La commande `Detach` permet de placer en mode hors connexion une base de données du serveur.  
  
## <a name="attach-and-detach-usage"></a>Utilisation des commandes Attach et Detach  
 La commande `Attach` est utilisée pour mettre en ligne une structure de base de données existante. Si la base de données est attachée en mode `ReadWrite`, elle ne peut être jointe qu'une seule fois à une instance de serveur. Toutefois, si la base de données est attachée en mode `ReadOnly`, elle peut être jointe plusieurs fois aux différentes instances de serveur. Par ailleurs, la même base de données ne peut pas être attachée plus d'une fois à la même instance de serveur. Une erreur est déclenchée en cas de tentative faite pour attacher la même base de données plusieurs fois, même si les données ont été copiées dans des dossiers distincts.  
  
> [!IMPORTANT]  
>  S'il a été demandé un mot de passe pour détacher la base de données, le même mot de passe est requis pour attacher la base de données.  
  
 La commande `Detach` est utilisée pour mettre hors connexion une structure de base de données existante. Lorsqu'une base de données est détachée, vous devez fournir un mot de passe pour protéger les métadonnées confidentielles.  
  
> [!IMPORTANT]  
>  Pour protéger le contenu des fichiers de données, vous devez utiliser une liste de contrôle d'accès pour le dossier, les sous-dossiers et les fichiers de données.  
  
 Lorsque vous détachez une base de données, le serveur suit les étapes ci-après.  
  
|Détachement d'une base de données en lecture/écriture|Détachement d'une base de données en lecture seule|  
|--------------------------------------|-------------------------------------|  
|1) Le serveur émet une demande de verrou CommitExclusive sur la base de données.<br />2) Le serveur attend que toutes les transactions en cours soient validées ou annulées.<br />3) Le serveur génère toutes les métadonnées dont il a besoin pour détacher la base de données.<br />4) La base de données est marquée comme supprimée.<br />5) Le serveur valide la transaction.|1) La base de données est marquée comme supprimée.<br />2) Le serveur valide la transaction.<br /><br /> <br /><br /> Remarque : le mot de passe qui sert à détacher la base de données ne peut pas être modifié pour une base de données en lecture seule. Une erreur est déclenchée si un paramètre de mot de passe est fourni pour une base de données attachée contenant déjà un mot de passe.|  
  
 Les commandes `Attach` et `Detach` doivent être exécutées comme de simples opérations. Elles ne peuvent pas être combinées à d'autres opérations de la même transaction. En outre, `Attach` les `Detach` commandes et sont des commandes transactionnelles atomiques. Cela signifie que soit l'opération réussit, soit elle échoue. Aucune base de données ne demeurera dans un état inachevé.  
  
> [!IMPORTANT]  
>  Les privilèges administrateur de serveur ou de base de données sont nécessaires pour exécuter la commande `Detach`.  
  
> [!IMPORTANT]  
>  Les privilèges d'administrateur de serveur sont requis pour exécuter la commande `Attach`.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 [Microsoft. AnalysisServices. Database. Detach *](/dotnet/api/microsoft.analysisservices.core.database.detach)   
 [Déplacer une base de données Analysis Services](move-an-analysis-services-database.md)   
 [ReadWriteModes de base de données](database-readwritemodes.md)   
 [Basculer une base de données Analysis Services entre les modes ReadOnly et ReadWrite](switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)   
 [Détacher l’élément](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element)   
 [Élément Attach](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element)  
  
  
