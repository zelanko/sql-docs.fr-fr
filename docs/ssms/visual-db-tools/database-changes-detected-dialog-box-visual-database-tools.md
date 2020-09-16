---
description: Modifications détectées dans la base de données, boîte de dialogue (Visual Database Tools)
title: Boîte de dialogue Modifications détectées dans la base de données
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.schema.databasechangesdetected
- vdtsql.chm:65543
- vdtsql.chm:65554
ms.assetid: 91f13086-371f-46a2-9f46-804c1415f3ed
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 3d063c559669e9dfe973485611895aff5d2d8688
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88497199"
---
# <a name="database-changes-detected-dialog-box-visual-database-tools"></a>Modifications détectées dans la base de données, boîte de dialogue (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Cette boîte de dialogue apparaît si vous essayez d’enregistrer un diagramme de base de données ou des tables sélectionnées, mais certains des objets de la base de données qui seront affectés par l’action d’enregistrement sont devenus obsolètes pour la base de données. Le fait d'accepter les modifications indiquées dans cette boîte de dialogue met à jour la base de données pour qu'elle corresponde à votre schéma et écrase les modifications des autres utilisateurs.  
  
> [!NOTE]  
> Bien que vous ne puissiez pas annuler les modifications apportées à une table ou à un diagramme de base de données, les modifications ne seront enregistrées dans la base de données que lorsque vous enregistrerez la table ou le diagramme. Vous pouvez ignorer les modifications non enregistrées en choisissant **Non** et en fermant tous les schémas ouverts sans les enregistrer.  
  
## <a name="options"></a>Options  
**Signaler les différences de détection**  
Spécifie si cette boîte de dialogue apparaît à la prochaine tentative d’enregistrement du diagramme de base de données ou des tables sélectionnées. Si l'option est activée, la boîte de dialogue continue d'apparaître chaque fois que vous enregistrez un schéma ou une table devenus obsolètes pour la base de données. Si l'option est désactivée, elle signifie que la boîte de dialogue n'apparaît pas. Par défaut, cette case est activée. Si vous décochez cette option, vous pouvez la recocher dans la boîte de dialogue **Options** .  
  
**Oui**  
Met à jour la base de données avec toutes les modifications indiquées dans la liste.  
  
**Non**  
Annule la demande d'enregistrement.  
  
> [!NOTE]  
> Pour actualiser votre schéma afin qu'il corresponde à la base de données, fermez-la sans enregistrer les modifications, cliquez avec le bouton droit sur le schéma dans l'Explorateur de serveurs et cliquez sur Actualiser, puis rouvrez le schéma.  
  
**Enregistrer comme fichier texte**  
Affiche la boîte de dialogue **Enregistrer sous** qui permet de spécifier un emplacement pour un fichier texte contenant une liste des modifications de la base de données.  
  
## <a name="see-also"></a>Voir aussi  
[Rapprocher un diagramme de base de données et une base de données modifiée &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/reconcile-a-database-diagram-with-a-modified-database-visual-database-tools.md)  
[Environnements multi-utilisateurs &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/multiuser-environments-visual-database-tools.md)  
  
