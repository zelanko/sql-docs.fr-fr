---
title: Boîte de dialogue Propriétés de DataSet, requête | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10160"
- sql12.rtp.rptdesigner.datasetproperties.query.f1
ms.assetid: 1fa34a4b-7de0-4e92-99fa-bc28a206773f
author: maggiesmsft
ms.author: maghan
manager: kfile
ms.openlocfilehash: f83cde4947e9734aa11a6758d19d056ce7e6a82c
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56011800"
---
# <a name="dataset-properties-dialog-box-query"></a>Boîte de dialogue Propriétés du dataset, Requête
  Sélectionnez **Requête** dans la boîte de dialogue **Propriétés du dataset** pour choisir une source de données et créer une requête.  
  
 La boîte de dialogue **Propriétés du dataset** inclut les éléments suivants :  
  
-   [Propriétés de jeux de données, boîte de dialogue, paramètres](report-data/dataset-properties-dialog-box-parameters.md)  
  
-   [Propriétés du dataset, boîte de dialogue (Champs)](../../2014/reporting-services/dataset-properties-dialog-box-fields.md)  
  
-   [Propriétés de jeux de données, boîte de dialogue, options](../../2014/reporting-services/dataset-properties-dialog-box-options.md)  
  
-   [Dataset Properties Dialog Box, Filters](report-data/dataset-properties-dialog-box-filters.md)  
  
## <a name="options"></a>Options  
 **Nom**  
 Tapez le nom du dataset. Ce nom doit être différent de celui des régions ou des groupes de données du rapport.  
  
 **Source de données**  
 Sélectionnez la source de données sur laquelle baser le dataset. Cliquez sur **Nouvelle**pour créer une nouvelle source de données.  
  
 **Type de requête**  
 Sélectionnez le type de commande ou de requête à utiliser pour le dataset. Sélectionnez **Texte** pour exécuter une requête afin d'extraire des données de la base de données. Sélectionnez **Table** pour utiliser la fonctionnalité **TableDirect** de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] afin de sélectionner tous les champs d'une table. Sélectionnez **Procédure stockée** pour exécuter une procédure stockée par nom. **Texte** est sélectionné par défaut et est utilisé pour la plupart des requêtes. Pour modifier la requête de source de données sélectionnée, cliquez sur **Concepteur de requêtes**.  
  
> [!NOTE]  
>  Les types de requêtes ne sont pas tous pris en charge par toutes les sources de données. Par exemple, le type **Table** n'est pris en charge que par les types de sources de données **OLE DB** et **ODBC**.  
  
 **Requête**  
 Cette option apparaît quand vous choisissez l’option de type de commande **Texte** . Tapez une requête ou importez-en une existante en cliquant sur **Importer**. Cliquez sur le bouton **Expression** (*fx*) pour modifier l’expression.  
  
> [!NOTE]  
>  Si vous avez utilisé un concepteur de requêtes pour générer une requête, le texte de celle-ci s'affiche dans cette zone.  
  
 **Nom de la table**  
 Entrez le nom de la table que vous souhaitez utiliser comme dataset. Cette option apparaît lorsque vous sélectionnez **Table**.  
  
 **Sélectionnez ou entrez un nom de procédure stockée**  
 Tapez ou choisissez le nom de la procédure stockée que vous souhaitez utiliser. Cliquez sur le bouton **Expression** (*fx*) pour modifier l’expression. Cette option apparaît lorsque vous choisissez l'option de type de commande Procédure stockée.  
  
 **Délai dépassé (en secondes)**  
 Tapez la valeur en secondes du délai d'expiration de la requête. La valeur par défaut est 30 secondes. La valeur de **Délai dépassé** doit être vide ou supérieure à zéro. Si elle ne contient aucune valeur, la requête n'est soumise à aucun délai d'expiration.  
  
## <a name="see-also"></a>Voir aussi  
 [Connexions de données, Sources de données et chaînes de connexion dans Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Ajouter des données à un rapport &#40;Générateur de rapports et SSRS&#41;](report-data/report-datasets-ssrs.md)   
 [Concepteurs de requêtes &#40;Générateur de rapports&#41;](../../2014/reporting-services/query-designers-report-builder.md)   
 [Concepteurs de requêtes Reporting Services](../../2014/reporting-services/reporting-services-query-designers.md)  
  
  
