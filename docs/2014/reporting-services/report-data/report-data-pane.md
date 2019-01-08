---
title: Volet des données de rapport
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.prod: reporting-services-2014, sql-server-2014
ms.prod_service: reporting-services-native, reporting-services-sharepoint
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: 1696ea3cb9fa238e3ac31418670a1d4195ab2e98
ms.sourcegitcommit: 2f5773f4bc02bfff4f2924226ac5651eb0c00924
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2018
ms.locfileid: "53553201"
---
# <a name="report-data-pane-in-sql-server-reporting-services-ssrs"></a>Volet données du rapport dans SQL Server Reporting Services (SSRS)

  Utilisez le volet **Données du rapport** pour consulter les paramètres, sources de données, datasets, collections de champs et images définis dans votre rapport. Le volet des données de rapportpropose une vue hiérarchique des éléments qui représentent les données de votre rapport. Les nœuds du niveau supérieur représentent les champs prédéfinis, paramètres et images, ainsi que les références de sources de données. Développez chaque nœud pour en afficher les éléments de données. Par exemple, lorsque vous développez un nœud de source de données, les datasets définis pour cette source de données apparaissent. Lorsque vous développez un dataset, sa collection de champs apparaît. Faites glisser des éléments vers l'aire de conception du rapport pour lier des données aux éléments de rapport de la page du rapport.  
  
## <a name="options"></a>Options

 **Champs prédéfinis**  
 Représente des champs fournis par Reporting Services et couramment utilisés dans un rapport, comme le nom du rapport ou le numéro de page. Pour plus d’informations, consultez [Collections intégrées dans les expressions &#40;Générateur de rapports et SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).  
  
 **Paramètres**  
 Représente la collection des paramètres de rapport, chacun pouvant correspondre à une valeur unique ou à plusieurs valeurs. Pour plus d'informations, consultez [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).  
  
 **Images**  
 Représente l'ensemble d'images utilisé dans le rapport. Pour plus d’informations, consultez [Images &#40;Générateur de rapports et SSRS&#41;](../report-design/images-report-builder-and-ssrs.md).  
  
 **Source de données**  
 Représente une référence de source de données unique à une source de données incorporée ou partagée. Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], les sources de données partagées apparaissent dans l’Explorateur de solutions, dans le dossier Sources de données partagées. Une source de données spécifie l'un des types de sources de données pris en charge par Reporting Services. Une source de données est le nœud parent de la collection de datasets auxquels elle sert de base. Pour plus d’informations, consultez [des connexions de données, les Sources de données et les chaînes de connexion dans Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) .  
  
 **Dataset**  
 Représente un dataset unique. Un dataset est le nœud parent de la collection de champs spécifiée par la requête et comprenant les champs calculés. Reporting Services prend en charge des concepteurs de requêtes qui vous aident dans la spécification des requêtes. Pour plus d’informations, consultez [ajouter des données à un rapport &#40;Générateur de rapports et SSRS&#41; ](report-datasets-ssrs.md) et [outils de conception de requête dans le rapport concepteur SQL Server Data Tools &#40;SSRS&#41;](query-design-tools-ssrs.md).  
  
## <a name="next-steps"></a>Étapes suivantes

 - [Collection de champs de dataset &#40;Générateur de rapports et SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)
 - [Volet de regroupement](../tools/grouping-pane.md)