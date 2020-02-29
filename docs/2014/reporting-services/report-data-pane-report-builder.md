---
title: Volet des données de rapport (Générateur de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10435"
helpviewer_keywords:
- Report Data pane
ms.assetid: 1492aa39-aeb1-4509-ab97-b9edd0901b7e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2a77024e62402cea0a37b945e0539274fee9a3c6
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78173328"
---
# <a name="report-data-pane-report-builder"></a>Volet des données de rapport (Générateur de rapports)
  Utilisez le volet **Données du rapport** pour consulter les paramètres, sources de données, datasets, collections de champs et images définis dans votre rapport. Le volet des données de rapportpropose une vue hiérarchique des éléments qui représentent les données de votre rapport. Les nœuds du niveau supérieur représentent les champs prédéfinis, paramètres et images, ainsi que les références de sources de données. Développez chaque nœud pour en afficher les éléments de données. Par exemple, lorsque vous développez un nœud de source de données, les datasets définis pour cette source de données apparaissent. Lorsque vous développez un dataset, sa collection de champs apparaît. Faites glisser des éléments vers l'aire de conception de rapport ou vers le volet Regroupement pour lier les données aux éléments de rapport sélectionnés dans la page du rapport. Pour plus d’informations, consultez [Mode Création de rapport &#40;Générateur de rapports&#41;](report-builder/report-design-view-report-builder.md).

## <a name="options"></a>Options
 **Champs prédéfinis** Représente les champs couramment utilisés dans un rapport, tels que le nom du rapport ou le numéro de page. Pour plus d’informations, consultez [Collections intégrées dans les expressions &#40;Générateur de rapports et SSRS&#41;](report-design/built-in-collections-in-expressions-report-builder.md).

 **Paramètres** Représente la collection de paramètres de rapport, chacun pouvant être à valeur unique ou à valeurs multiples. Pour plus d'informations, consultez [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](report-design/report-parameters-report-builder-and-report-designer.md).

 **Images** Représente l’ensemble d’images utilisé dans le rapport. Pour plus d’informations, consultez [Images &#40;Générateur de rapports et SSRS&#41;](report-design/images-report-builder-and-ssrs.md).

 **Sources de données** Représente une source de données incorporée ou une référence à une source de données partagée. Une source de données représente une source de données pour le rapport. Une source de données est le nœud parent de la collection de datasets qui l'utilise. Pour plus d’informations, consultez [Ajouter des données à un rapport &#40;générateur de rapports et SSRS&#41;](report-data/report-datasets-ssrs.md) et [connexions de données, sources de données et chaînes de connexion dans générateur de rapports](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md).

 **Jeux de données** Représente les données récupérées d’une source de données en exécutant une commande, par exemple, une [!INCLUDE[tsql](../includes/tsql-md.md)] requête qui extrait des données d’une [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] base de données. Un dataset est le nœud parent de la collection de champs spécifiée par la requête et comprend également des champs calculés. Le Générateur de rapports prend en charge des concepteurs de requêtes qui vous aident dans la spécification des requêtes. Pour plus d’informations, consultez [Ajouter des données à un rapport &#40;générateur de rapports et SSRS&#41;](report-data/report-datasets-ssrs.md).

## <a name="see-also"></a>Voir aussi
 [Collection de champs de Dataset &#40;générateur de rapports et SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md) [Générateur de rapports aide pour les boîtes de dialogue, les volets et le volet de regroupement des assistants](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) [&#40;](report-design/grouping-pane-report-builder.md) générateur de rapports&#41;la [recherche, l’affichage et la gestion des rapports &#40;générateur de rapports et SSRS &#41;](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)


