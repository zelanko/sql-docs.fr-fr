---
description: Enregistrer des tables sélectionnées dans un schéma (Visual Database Tools)
title: Enregistrer des tables sélectionnées dans un schéma
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- saving tables
ms.assetid: 86943b49-48f3-432c-8021-928c13edfbcf
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 9aea9e1ec6db770bc7c44f8b7a790c0564773beb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88460012"
---
# <a name="save-selected-tables-on-a-diagram-visual-database-tools"></a>Enregistrer des tables sélectionnées dans un schéma (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Si vous ne souhaitez pas enregistrer toutes les modifications que vous avez apportées à un diagramme de base de données, vous pouvez enregistrer une table ou un groupe de tables spécifique.  
  
### <a name="to-save-selected-tables"></a>Pour enregistrer les tables sélectionnées  
  
1.  Dans votre diagramme de base de données, sélectionnez les tables que vous voulez enregistrer.  
  
2.  Dans le menu **Fichier** , cliquez sur **Enregistrer la sélection**.  
  
3.  La boîte de dialogue **Enregistrer** affiche la liste des tables qui seront mises à jour dans la base de données quand vous enregistrerez votre sélection.  
  
    Choisissez **Enregistrer comme fichier texte** si vous voulez enregistrer la liste des tables dans un fichier texte à l’intérieur du répertoire du projet avant de continuer.  
  
4.  Dans la boîte de dialogue **Enregistrer** , vérifiez la liste des tables et choisissez **Oui** pour enregistrer ces tables.  
  
    > [!NOTE]  
    > La liste des tables peut contenir d'autres tables en plus de celles que vous avez sélectionnées. Par exemple, si vous changez le type de données d'une colonne qui participe à une relation avec une autre table, les deux tables seront incluses dans cette liste.  
  
## <a name="see-also"></a>Voir aussi  
[Utiliser des diagrammes de base de données](../../ssms/visual-db-tools/work-with-database-diagrams-visual-database-tools.md)  
  
