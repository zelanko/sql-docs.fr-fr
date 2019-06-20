---
title: Incorporée et partagée des connexions de données ou Sources de données (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- embedded data sources
- shared data sources
- data sources
ms.assetid: f417782c-b85a-4c4d-8a40-839176daba56
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b987dd46f6a60a0d0cadc95cf187566eafa4f527
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66109271"
---
# <a name="embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs"></a>Connexions de données ou sources de données incorporées et partagées (Générateur de rapports et SSRS)
  Les rapports utilisent des connexions de données pour récupérer les données nécessaires lorsqu'une requête s'exécute ou lorsque le rapport est traité. Dans la liste correspondante, choisissez un type de connexion de données intégré pour vous connecter à une base de données relationnelle, une base de données multidimensionnelle, un service Web ou toute autre source de données. Les termes suivants sont utilisés lors de la description des connexions de données.  
  
-   **Connexion de données.** Également appelée *Source de données*. Une connexion de données inclut un nom et des propriétés de connexion qui dépendent du type de connexion. Par défaut, une connexion de données n'inclut pas d'informations d'identification. Une connexion de données ne spécifie pas les données à récupérer à partir de la source de données externe. Pour ce faire, vous devez spécifier une requête lorsque vous créez un dataset.  
  
-   **Définition de source de données.** Un fichier qui contient la représentation XML d'une source de données de rapport. Lorsqu'un rapport est publié, ses sources de données sont enregistrées sur le serveur de rapports ou le site SharePoint en tant que définitions de source de données, indépendamment de la définition de rapport. Par exemple, un administrateur de serveur de rapports peut mettre à jour la chaîne de connexion ou les informations d'identification. Sur un serveur de rapports natif, le type de fichier est .rds. Sur un site SharePoint, le type de fichier est .rsds.  
  
-   **Chaîne de connexion.** Une chaîne de connexion est une version de chaîne des propriétés de connexion nécessaires à la connexion à une source de données. Les propriétés de connexion diffèrent selon le type de connexion de données. Pour obtenir des exemples, consultez [des connexions de données, les Sources de données et les chaînes de connexion dans le Générateur de rapports](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md).  
  
-   **Source de données partagée.** Source de données disponible sur un serveur de rapports ou un site SharePoint, et qui est utilisable par plusieurs rapports.  
  
-   **Source de données incorporée.** Également appelée *source de données spécifique aux rapports*. Il s'agit d'une source de données définie dans un rapport et utilisée uniquement par ce dernier.  
  
-   **Informations d'identification.** Les informations d'identification sont des informations d'authentification qui doivent être fournies pour vous permettre d'accéder à des données externes.  
  
 La différence entre les deux sources de données réside dans leur mode de création, de stockage et de gestion.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
## <a name="shared-data-sources"></a>Sources de données partagées  
 Les sources de données partagées sont utiles lorsque vous disposez de sources de données que vous utilisez souvent. Il est recommandé d'utiliser des sources de données partagées dans la mesure du possible. Celles-ci permettent de gérer plus facilement les rapports et l'accès aux rapports, et de sécuriser davantage les rapports et les sources de données auxquelles ils accèdent. Si vous avez besoin d'une source de données partagée, demandez à votre administrateur système d'en créer une pour vous.  
  
 Dans le Générateur de rapports, vous ne pouvez pas créer de source de données partagée. Vous pouvez rechercher et sélectionner une source de données partagée à partir du serveur de rapports. Pour plus d'informations, consultez [Data Connections, Data Sources, and Connection Strings in Report Builder](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md).  
  
 Dans le Concepteur de rapports, vous ne pouvez pas rechercher une source de données partagée située sur le serveur de rapports. Vous pouvez créer des sources de données partagées dans le cadre d'un projet au sein de l'Explorateur de solutions, puis déterminer s'il convient de les déployer sur un serveur de rapports. Vous pouvez choisir de les utiliser localement uniquement, en raison des différences en matière d'informations d'identification requises sur votre ordinateur ou le serveur de rapports. Pour plus d’informations, consultez [Connexions de données, sources de données et chaînes de connexion dans Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md).  
  
 L'icône suivante indique un élément de source de données partagée dans l'arborescence des dossiers du serveur de rapports : ![Icône Source de données partagée](media/hlp-16datasource.png "Icône Source de données partagée")  
  
## <a name="embedded-data-sources"></a>Sources de données incorporées  
 Une source de données incorporée est une connexion de données enregistrée dans la définition de rapport. Les informations de connexion à la source de données incorporée peuvent être utilisées uniquement par le rapport dans lequel elles sont incorporées. Pour définir et gérer des sources de données incorporées, utilisez la boîte de dialogue **Propriétés de la source de données** .  
  
##  <a name="Comparing"></a> Comparaison incorporé et Sources de données partagées  
 Le tableau suivant indique les différences entre les sources de données incorporées et partagées :  
  
|Description|Source de données<br /><br /> Source de données|Partagés<br /><br /> Source de données|  
|-----------------|------------------------------|----------------------------|  
|La connexion de données est incorporée dans la définition de rapport.|![Disponible](media/greencheck.gif "Disponible")||  
|Le pointeur vers la connexion de données sur le serveur de rapports est incorporé dans la définition de rapport.||![Disponible](media/greencheck.gif "Disponible")|  
|Gestion sur le serveur de rapports|![Disponible](media/greencheck.gif "Disponible")|![Disponible](media/greencheck.gif "Disponible")|  
|Obligatoire pour les datasets partagés||![Disponible](media/greencheck.gif "Disponible")|  
|Obligatoire pour les composants||![Disponible](media/greencheck.gif "Disponible")|  
  
## <a name="data-source-credentials"></a>Informations d'identification de la source de données  
 Les informations d'identification sont utilisées pour créer une source de données incorporée, exécuter une requête ou récupérer des données lors du traitement d'un rapport. Le propriétaire de la source de données détermine le type d'informations d'identification à utiliser pour accéder aux données. Les informations d'identification sont gérées indépendamment de la connexion de données sur un serveur de rapports, un site SharePoint ou un ordinateur local, au sein d'un environnement de création de rapports. Selon le type de source de données, les informations d'identification peuvent être enregistrées à des fins d'automatisation, ou définies pour être demandées à chaque utilisateur. Les informations d'identification nécessaires peuvent différer selon que vous vous connectez à la source de données à partir de votre ordinateur ou à partir du serveur de rapports. Pour plus d’informations, consultez [spécifier les informations d’identification dans le Générateur de rapports](../../2014/reporting-services/specify-credentials-in-report-builder.md) et [des connexions de données, les Sources de données et les chaînes de connexion dans Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des données à un rapport &#40;Générateur de rapports et SSRS&#41;](report-data/report-datasets-ssrs.md)   
 [Concepts de création de rapport &#40;Générateur de rapports et SSRS&#41;](report-design/report-authoring-concepts-report-builder-and-ssrs.md)   
 [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md)   
 [Ajouter et vérifier une connexion de données ou d’une Source de données &#40;Générateur de rapports et SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)   
 [Datasets incorporés et partagés &#40;Générateur de rapports et SSRS&#41;](report-data/embedded-and-shared-datasets-report-builder-and-ssrs.md)  
  
  
