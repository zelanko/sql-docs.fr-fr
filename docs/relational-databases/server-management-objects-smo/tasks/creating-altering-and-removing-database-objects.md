---
title: Utilisation des objets de base de données | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- database objects [SMO]
- objects [SMO]
ms.assetid: 702fd63d-8734-4a02-872e-aecfb037c787
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: db9333ec36ce9993ff0b8e3199ce5288a945d5e7
ms.sourcegitcommit: f3f83ef95399d1570851cd1360dc2f072736bef6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "70148528"
---
# <a name="creating-altering-and-removing-database-objects"></a>Création, modification et suppression d’objets de base de données
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Les étapes de la création d'objets SMO sont les suivantes :  
  
1.  Créer une instance de l'objet.  
  
2.  Définir les propriétés de l'objet.  
  
3.  Créer les instances des objets enfants.  
  
4.  Définir les propriétés des objets enfants.  
  
5.  Créer l'objet.  

[!INCLUDE[freshInclude](../../../includes/paragraph-content/fresh-note-steps-feedback.md)]

 Lorsque les instances d'objets SMO sont créées dans une application SMO, ils n'existent pas sur l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , jusqu'à ce que la méthode **Create** soit émise. Toutefois, il n'est pas nécessaire d'émettre une méthode **Create** pour chaque objet individuel. Si un objet possède un jeu d'objets enfants, seul l'objet parent est requis pour exécuter la méthode **Create** . Par exemple, la définition d'une table nécessite qu'elle contienne au moins une colonne. De même, une colonne ne peut pas exister séparément d'une table. Il existe une relation de codépendance entre la table et ses colonnes.  
  
 La méthode <xref:Microsoft.SqlServer.Management.Dmf.Policy.Alter%2A> permet d'apporter des modifications à un objet. Plusieurs modifications d'un objet, telles que l'ajout d'objets enfants à l'une des collections de l'objet ou la modification d'une valeur de propriété, sont regroupées et exécutées comme un tout. La méthode **Alter** réduit le trafic réseau et améliore les performances globales.  
  
 L'instruction **Drop** est utilisée pour supprimer un objet et tous ses objets enfants codépendants requis pour créer initialement l'objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle objet SMO](../../../relational-databases/server-management-objects-smo/smo-object-model.md)  
  
  
