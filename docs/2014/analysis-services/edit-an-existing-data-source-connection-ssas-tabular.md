---
title: Modifier une connexion de Source de données existante (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.selexistconn.f1
ms.assetid: 97e63f18-a01d-4c91-a411-e7e6d40a0647
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ffc45b255ef609d486f19cf18254ad9ed2937433
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66081452"
---
# <a name="edit-an-existing-data-source-connection-ssas-tabular"></a>Modifier une connexion à une source de données existante (SSAS Tabulaire)
  Cette rubrique décrit la procédure de modification des propriétés d'une connexion de source de données existante dans un modèle tabulaire.  
  
 Après avoir créé une connexion à une source de données externe, vous pouvez modifier cette connexion des différentes façons suivantes :  
  
-   Vous pouvez modifier les informations de la connexion, notamment le fichier, le flux ou la base de données utilisés comme source, ses propriétés ou d'autres options de connexion spécifiques du fournisseur.  
  
-   Vous pouvez modifier les mappages de tables et de colonnes et supprimer des références aux colonnes qui ne sont plus utilisées.  
  
-   Vous pouvez modifier les tables, les vues et les colonnes que vous obtenez à partir de la source de données externe.  
  
## <a name="modify-a-connection"></a>Modifier une connexion  
 Cette procédure décrit comment modifier une connexion de source de données de base de données. Certaines options relatives à l'utilisation des sources de données diffèrent selon le type de source de données ; toutefois, vous devez pouvoir identifier facilement ces différences.  
  
#### <a name="to-change-the-external-data-source-used-by-a-current-connection"></a>Pour modifier la source de données externe utilisée par une connexion actuelle  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], cliquez sur le menu **Modèle** , puis sur **Connexions existantes**.  
  
2.  Sélectionnez la connexion à la source de données que vous souhaitez modifier, puis cliquez sur **Modifier**.  
  
3.  Dans la boîte de dialogue **Modifier la connexion** , cliquez sur **Parcourir** pour localiser une autre base de données du même type avec un nom ou un emplacement différent.  
  
     Dès que vous modifiez le fichier de base de données, un message apparaît pour indiquer que vous devez enregistrer et actualiser les tables pour afficher les nouvelles données.  
  
4.  Cliquez sur **Enregistrer**, puis sur **Fermer**.  
  
5.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur **Modèle**, sur **Traiter**, puis sur **Traiter tout**.  
  
     Les tables sont retraitées à l'aide de la nouvelle source de données, mais avec les sélections de données d'origine.  
  
    > [!NOTE]  
    >  Si la nouvelle source de données contient des tables supplémentaires qui n'étaient pas présentes dans la source de données d'origine, vous devez rouvrir la connexion modifiée et ajouter les tables.  
  
## <a name="edit-table-and-column-mappings-bindings"></a>Modifier les mappages de tables et de colonnes (liaisons)  
 Cette procédure décrit comment modifier les mappages après avoir modifié une source de données.  
  
#### <a name="to-edit-column-mappings-when-a-data-source-changes"></a>Pour modifier des mappages de colonnes lorsqu'une source de données change  
  
1.  Dans le générateur de modèles, sélectionnez une table.  
  
2.  Cliquez sur le menu **Table** , puis sur **Propriétés de la table**.  
  
     Le nom de la table sélectionnée est affiché dans la zone **Nom de la table** . La zone **Nom de la source** contient le nom de la table dans la source de données externe. Si des colonnes sont nommées différemment dans la source et dans le modèle, vous pouvez basculer entre les deux ensembles de noms de colonnes en sélectionnant les options **Source** ou **Modèle**.  
  
3.  Pour changer la table utilisée comme source de données, sélectionnez une autre table dans la zone **Nom de la source**.  
  
4.  Modifiez les mappages de colonnes si nécessaire :  
  
    1.  Pour ajouter des colonnes qui sont présentes dans la source mais pas dans le modèle, activez la case à cocher en regard du nom des colonnes.  
  
         Les données effectives seront chargées dans le modèle lors de la prochaine actualisation des données.  
  
    2.  Si certaines colonnes du modèle ne sont plus disponibles dans la source de données actuelle, un message s'affiche dans la zone de notification, répertoriant les colonnes non valides. Vous n'avez pas besoin de faire autre chose.  
  
5.  Cliquez sur **Enregistrer** pour appliquer les modifications à votre modèle.  
  
     Lorsque vous enregistrez l'ensemble actuel de propriétés de table, un message peut apparaître pour vous prévenir que vous devez traiter les tables. Cliquez sur **Traiter** pour charger les données mises à jour dans votre modèle.  
  
## <a name="see-also"></a>Voir aussi  
 [Traiter les données &#40;SSAS Tabulaire&#41;](process-data-ssas-tabular.md)   
 [Sources de données prises en charge &#40;SSAS Tabulaire&#41;](tabular-models/data-sources-supported-ssas-tabular.md)  
  
  
