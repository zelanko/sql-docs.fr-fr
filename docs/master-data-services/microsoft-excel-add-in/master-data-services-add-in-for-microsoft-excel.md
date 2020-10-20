---
title: Vue d’ensemble
description: Découvrez comment charger des données à partir de Master Data Services dans Excel et les publier sur Master Data Services à l’aide de l’Complément Master Data Services pour Excel.
ms.custom: microsoft-excel-add-in, seo-lt-2019
ms.date: 07/25/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 33d9c8fc-9602-494d-b9ab-8f0f42785974
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ec0059471e10db953db26cfdd4c7b620a3378316
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "92257792"
---
# <a name="master-data-services-add-in-for-microsoft-excel"></a>Complément Master Data Services pour Microsoft Excel

[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]vous permet de charger des listes filtrées de données à partir de MDS dans Excel et de les utiliser comme tout autre type de données. Lorsque vous avez terminé, vous pouvez de nouveau publier les données sur MDS, où elles sont stockées de manière centralisée. La sécurité détermine les données que vous pouvez afficher et mettre à jour.  
  
 Si vous êtes un administrateur, utilisez [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] pour créer des entités et des attributs et les charger avec des données. Cela vous évite d'utiliser d'autres outils pour charger les données dans vos modèles.  
  
 Dans [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], vous pouvez utiliser Data Quality Services (DQS) pour faire correspondre des données avant de les charger dans MDS. Cela évite la duplication des données dans MDS.  

## <a name="downloads"></a>Téléchargements 
>*  Téléchargez le complément Master Data Services pour Excel pour SQL Server 2016 SP2 depuis cette [page du Centre de téléchargement Microsoft](https://www.microsoft.com/download/details.aspx?id=56838). 
>* Téléchargez le [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] pour SQL Server 2017 à partir de [cette page du Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/?linkid=836867).
>*  Téléchargez le Complément Master Data Services pour Excel pour SQL Server CTP 2019 à partir de [cette page du centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/?linkid=2086948). 
 
  
## <a name="terms"></a>Termes  
 Si vous utilisez le complément, vous devez connaître les termes suivants. Pour plus d’informations sur ces concepts, consultez [Vue d’ensemble de Master Data Services &#40;MDS&#41;](../../master-data-services/master-data-services-overview-mds.md).  
  
-   Le *référentiel MDS* est l'emplacement où toutes les données de référence sont stockées. Il s'agit d'une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configurée pour stocker des données MDS. Pour manipuler des données à partir du référentiel, vous devez les charger dans Excel, puis quand vous avez terminé votre travail, vous pouvez publier vos modifications dans le référentiel. Les administrateurs peuvent ajouter de nouvelles entités et de nouveaux attributs au référentiel.  
  
-   Les données*gérées par MDS* sont les données stockées dans le référentiel MDS que vous chargez dans Excel, les données étant affichées sous la forme de lignes en surbrillance. Vous pouvez ajouter des données non managées MDS à votre feuille de calcul, dans ce cas, celles-ci ne seront pas concernées par l'actualisation des données managées MDS.  
  
-   Un *modèle* est un conteneur de données. Plusieurs versions de ces conteneurs peuvent être créées, généralement la dernière version est aussi la plus récente. Pour plus d’informations, consultez [Modèles &#40;Master Data Services&#41;](../../master-data-services/models-master-data-services.md).  
  
-   Une *entité* est une liste de données. Vous pouvez considérer une entité comme une table d'une base de données. Par exemple, l'entité **Couleur** peut contenir une liste de couleurs. Pour plus d’informations, consultez [Entités &#40;Master Data Services&#41;](../../master-data-services/entities-master-data-services.md).  
  
-   Un *membre* est une ligne de données (enregistrement). Chaque entité contient des membres. Un membre est **Bleu**. Pour plus d’informations, consultez [Membres &#40;Master Data Services&#41;](../../master-data-services/members-master-data-services.md).  
  
-   Un *attribut* est une colonne de données. Chaque membre possède des attributs. Par exemple, l’attribut de **code** pour le membre **bleu** est **B**. Pour plus d’informations sur les attributs, consultez [attributs &#40;Master Data Services&#41;](../../master-data-services/attributes-master-data-services.md).  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Créez une connexion à un référentiel [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .|[Se connecter à un référentiel MDS &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md)|  
|Chargez les données managées MDS dans Excel.|[Export Data to Excel from Master Data Services](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md)|  
|Enregistrez une requête de raccourci que vous pouvez utiliser à l'avenir pour ouvrir les données managées MDS actuellement affichées.|[Enregistrer un fichier de requête de raccourci &#40;Complément MDS pour Excel#41;](../../master-data-services/microsoft-excel-add-in/save-a-shortcut-query-file-mds-add-in-for-excel.md)|  
|Partager des raccourcis avec d'autres utilisateurs.|[Envoyer par e-mail un fichier de requête de raccourci &#40;Complément MDS pour Excel#41;](../../master-data-services/microsoft-excel-add-in/email-a-shortcut-query-file-mds-add-in-for-excel.md)|  
|Afficher toutes les modifications apportées à un membre.|[Afficher toutes les annotations ou transactions pour un membre &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md)|  
|Avant de publier de nouvelles données, vérifier si certaines sont dupliquées.|[Mettre en correspondance les données similaires &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/match-similar-data-mds-add-in-for-excel.md)|  
|Publier les données d'une feuille de calcul dans le référentiel MDS.|[Publier des données d’Excel dans MDS &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)|  
|Créer une nouvelle entité avec les données dans la feuille de calcul. (Administrateurs uniquement.)|[Créer une entité &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/create-an-entity-mds-add-in-for-excel.md)|  
|Créez un attribut basé sur un domaine, également appelé une liste contrainte. (Administrateurs uniquement.)|[Créer un attribut basé sur un domaine &#40;complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/create-a-domain-based-attribute-mds-add-in-for-excel.md)|  
|Définissez les propriétés de chargement et de publication des données dans le complément Master Data Services pour Excel. (Administrateurs uniquement.)|[Définition des propriétés pour le complément Master Data Services pour Excel](../../master-data-services/microsoft-excel-add-in/setting-properties-for-master-data-services-add-in-for-excel.md)|  
  
## <a name="related-content"></a>Contenu associé  
  
-   [Connexions &#40;Complément MDS pour Excel#41;](../../master-data-services/microsoft-excel-add-in/connections-mds-add-in-for-excel.md)  
  
-   [Vue d’ensemble : exportation de données vers Excel &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
-   [Fichiers de requête de raccourci &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [Actualisation des données &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/refreshing-data-mds-add-in-for-excel.md)  
  
-   [Vue d’ensemble : importation de données à partir d’Excel &#40;complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
-   [Validation des données &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/validating-data-mds-add-in-for-excel.md)  
  
-   [Mise en correspondance de la qualité des données dans le complément MDS pour Excel](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)  
  
-   [Génération d’un modèle &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/building-a-model-mds-add-in-for-excel.md)  
  
-   [Définition des propriétés pour le complément Master Data Services pour Excel](../../master-data-services/microsoft-excel-add-in/setting-properties-for-master-data-services-add-in-for-excel.md)  
  
-   [Sécurité &#40;Master Data Services&#41;](../../master-data-services/security-master-data-services.md)  
  
  
