---
title: Sélectionner les tables et les vues sources (Assistant Importation et Exportation SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.selectsourcetablesandviews.f1
ms.assetid: f60e1a19-2ea6-403c-89ab-3e60ac533ea0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6356cb594013d642741148dd85f7ddefc1e08ff0
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85436746"
---
# <a name="select-source-tables-and-views-sql-server-import-and-export-wizard"></a>Sélectionner les tables et les vues sources (Assistant Importation et Exportation SQL Server)
  Utilisez la page **Sélectionner les tables et les vues sources** pour spécifier les tables et les vues à copier de la source de données vers la destination.  
  
> [!NOTE]  
>  Vous n'êtes pas obligé de copier toutes les colonnes d'une table lorsque vous sélectionnez l'option de copie de table. Après avoir sélectionné une table de destination, cliquez sur modifier les mappages pour afficher la boîte de dialogue **mappage de colonnes** . Sélectionnez **\<ignore>** dans la colonne **destination** de la boîte de dialogue **mappage de colonnes** pour les colonnes que vous souhaitez ignorer.  
  
 Pour en savoir plus sur cet Assistant, consultez [Assistant Importation et Exportation SQL Server](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Pour en savoir plus sur les options de démarrage de l’Assistant et sur les autorisations requises pour exécuter correctement l’Assistant, consultez [exécuter l’Assistant importation et exportation SQL Server](start-the-sql-server-import-and-export-wizard.md).  
  
 La fonction de l'Assistant Importation et Exportation SQL Server est de copier des données d'une source vers une destination. L'Assistant peut également créer une base de données de destination et des tables de destination à votre intention. Toutefois, si vous devez copier plusieurs tables ou bases de données, ou autres types d'objets de bases de données, vous devez plutôt utiliser l'Assistant Copie de base de données. Pour plus d'informations, consultez [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Options  
  
### <a name="tables-and-views-list"></a>Liste Tables et vues  
 **Source**  
 Activez les cases à cocher pour sélectionner dans la liste les tables et les vues à copier. Si vous sélectionnez une table ou une vue source sans effectuer d'autre action, vous copiez le schéma et les données de la source sans modification.  
  
 **Destination**  
 Sélectionnez dans la liste une table de destination pour chaque table source.  
  
> [!NOTE]  
>  Si vous faites une pause à ce stade de l'Assistant pour créer une table de destination dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ou d'un autre outil, la nouvelle table n'est pas visible immédiatement dans la liste des tables de destination disponibles. Pour actualiser la liste des tables de destination, effectuez un pas à pas principal dans la page **choisir une destination** , resélectionnez la base de données de destination, puis revenez en arrière jusqu’à la page **Sélectionner les tables et les vues sources**.  
  
### <a name="other-options"></a>Autres options  
 **Modifier les mappages**  
 Utilisez la boîte de dialogue **mappage de colonnes** pour spécifier les colonnes de destination qui recevront les données sources. Vous pouvez copier uniquement un sous-ensemble de colonnes en sélectionnant \<ignore> dans la colonne **destination** de la boîte de dialogue **mappage** de colonnes les colonnes que vous souhaitez ignorer.  
  
 **Préversion**  
 Affichez un aperçu des données sources dans la boîte de dialogue **aperçu des données** pour les vérifier avant d’effectuer l’importation ou l’exportation. La boîte de dialogue **aperçu des données** affiche jusqu’à 200 lignes de données.  
  
 Après l'aperçu des données, vous pouvez à votre guise modifier les options que vous avez sélectionnées pour la source et la destination des données. Pour effectuer ces modifications, dans la page **Sélectionner les tables et les vues sources**, cliquez sur **Précédent** pour retourner aux pages précédentes où vous pouvez modifier vos sélections.  
  
  
