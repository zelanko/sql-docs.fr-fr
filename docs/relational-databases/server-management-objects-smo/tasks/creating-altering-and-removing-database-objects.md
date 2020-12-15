---
description: Création, modification et suppression d’objets de base de données
title: Utilisation des objets de base de données
ms.custom: seo-dt-2019
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
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f2ae7dbbfc762ed342ddc085afcb799f9b292966
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97468500"
---
# <a name="creating-altering-and-removing-database-objects"></a>Création, modification et suppression d’objets de base de données
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

  Les étapes de la création d'objets SMO sont les suivantes :  
  
1.  Créer une instance de l'objet.  
  
2.  Définir les propriétés de l'objet.  
  
3.  Créer les instances des objets enfants.  
  
4.  Définir les propriétés des objets enfants.  
  
5.  Créer l'objet.  

 Lorsque les instances d'objets SMO sont créées dans une application SMO, ils n'existent pas sur l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , jusqu'à ce que la méthode **Create** soit émise. Toutefois, il n'est pas nécessaire d'émettre une méthode **Create** pour chaque objet individuel. Si un objet possède un jeu d'objets enfants, seul l'objet parent est requis pour exécuter la méthode **Create** . Par exemple, la définition d'une table nécessite qu'elle contienne au moins une colonne. De même, une colonne ne peut pas exister séparément d'une table. Il existe une relation de codépendance entre la table et ses colonnes.  
  
 La méthode <xref:Microsoft.SqlServer.Management.Dmf.Policy.Alter%2A> permet d'apporter des modifications à un objet. Plusieurs modifications d'un objet, telles que l'ajout d'objets enfants à l'une des collections de l'objet ou la modification d'une valeur de propriété, sont regroupées et exécutées comme un tout. La méthode **Alter** réduit le trafic réseau et améliore les performances globales.  
  
 L'instruction **Drop** est utilisée pour supprimer un objet et tous ses objets enfants codépendants requis pour créer initialement l'objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle objet SMO](../../../relational-databases/server-management-objects-smo/smo-object-model.md)  
  
  
