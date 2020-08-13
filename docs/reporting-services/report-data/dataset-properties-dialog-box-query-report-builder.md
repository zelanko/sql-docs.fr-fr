---
title: Boîte de dialogue Propriétés du dataset, Requête (Générateur de rapports) | Microsoft Docs
description: Découvrez comment utiliser Requête dans la boîte de dialogue Propriétés du dataset dans le Générateur de rapports afin de choisir un jeu de données partagé dans un serveur de rapports ou de créer un jeu de données incorporé.
ms.date: 08/17/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: reference
f1_keywords:
- "10024"
- sql13.rtp.rptdesigner.datasetproperties.query.f1
- "10160"
ms.assetid: 75432318-0b00-4797-917c-0a2e74f9d951
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 14380ba698101c76a84d0b9eef27a4ea31953f2d
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86458931"
---
# <a name="dataset-properties-dialog-box-query-report-builder"></a>Boîte de dialogue Propriétés du dataset, Requête (Générateur de rapports)
 
Sélectionnez **Requête** dans la boîte de dialogue **Propriétés du dataset** afin de choisir un dataset partagé dans un serveur de rapports ou de créer un dataset incorporé. Dans le cas d'un dataset incorporé, vous devez choisir une source de données et générer une requête.  
  
## <a name="options"></a>Options  
 **Nom**  
 Tapez le nom du dataset. Ce nom doit être différent de celui des régions ou des groupes de données du rapport.  
  
 **Utiliser un dataset partagé**  
 Sélectionnez cette option pour utiliser un dataset prédéfini du serveur de rapports.  
  
 **Parcourir**  
 Recherchez un dossier sur un serveur de rapports ou un site SharePoint, puis sélectionnez un dataset partagé (.rsd).  
  
 **Utiliser un dataset incorporé dans mon rapport**  
 Sélectionnez cette option pour créer un dataset à utiliser uniquement par ce rapport.  
  
 **Source de données**  
 Sélectionnez la source de données sur laquelle baser le dataset. Cliquez sur **Nouvelle**pour créer une nouvelle source de données.  
  
 **Type de requête**  
 Sélectionnez le type de commande ou de requête à utiliser pour le dataset. Sélectionnez **Texte** pour exécuter une requête afin d'extraire des données de la base de données. Sélectionnez **Table** pour utiliser la fonctionnalité **TableDirect** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin de sélectionner tous les champs d'une table. Sélectionnez **Procédure stockée** pour exécuter une procédure stockée par nom. **Texte** est sélectionné par défaut et est utilisé pour la plupart des requêtes. Pour modifier la requête de source de données sélectionnée, cliquez sur **Concepteur de requêtes**.  
  
> [!NOTE]  
>  Les types de requêtes ne sont pas tous pris en charge par toutes les sources de données. Par exemple, le type **Table** n'est pris en charge que par les types de sources de données **OLE DB** et **ODBC**.  
  
 **Requête**  
 Cette option apparaît quand vous choisissez l’option de type de commande **Texte** . Tapez une requête ou importez-en une existante en cliquant sur **Importer**. Cliquez sur le bouton **Expression** (*fx*) pour modifier l’expression.  
  
> [!NOTE]  
>  Si vous utilisez un concepteur de requêtes pour générer une requête, le texte de celle-ci s’affiche dans cette zone.  
  
**Nom de la table**  
Cette option apparaît lorsque vous sélectionnez **Table**. Entrez le nom de la table que vous souhaitez utiliser comme dataset.   
  
**Sélectionnez ou entrez un nom de procédure stockée**  
Cette option apparaît lorsque vous choisissez l'option de type de commande Procédure stockée. Tapez ou choisissez le nom de la procédure stockée que vous souhaitez utiliser. Cliquez sur le bouton **Expression** (*fx*) pour modifier l’expression.   
  
 **Délai dépassé (en secondes)**  
 Tapez la valeur en secondes du délai d'expiration de la requête. La valeur par défaut est 30 secondes. La valeur de **Délai dépassé** doit être vide ou supérieure à zéro. Si elle ne contient aucune valeur, la requête n'est soumise à aucun délai d'expiration.  
  
 **Actualiser les champs**  
 Exécutez la commande de requête pour mettre à jour la liste de champs dans la page **Boîte de dialogue Propriétés du dataset, Champs**.  
  
## <a name="see-also"></a>Voir aussi  
[Datasets incorporés dans les rapports et datasets partagés &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
[Datasets de rapport &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)  
[Outils de création de requêtes &#40;SSRS&#41;](query-design-tools-ssrs.md)  
  
  
