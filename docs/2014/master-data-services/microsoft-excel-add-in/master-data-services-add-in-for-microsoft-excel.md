---
title: Complément Master Data Services pour Microsoft Excel | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 33d9c8fc-9602-494d-b9ab-8f0f42785974
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f84048371eac930974ebbd3d0693e25761f9a784
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84961159"
---
# <a name="master-data-services-add-in-for-microsoft-excel"></a>Complément Master Data Services pour Microsoft Excel
  Avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] , les listes principales de données de référence peuvent être distribuées à tous les membres de votre organisation qui utilisent Excel. La sécurité détermine quels utilisateurs peuvent afficher et mettre à jour les données.  
  
 Vous pouvez charger les listes filtrées de données MDS dans Excel, et les utiliser comme de la même façon que d'autres données. Lorsque vous avez terminé, vous pouvez de nouveau publier les données sur MDS, où elles sont stockées de manière centralisée.  
  
 Si vous êtes un administrateur, utilisez [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] pour créer des entités et des attributs et les charger avec des données. Cela vous évite d'utiliser d'autres outils pour charger les données dans vos modèles.  
  
 Dans [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], vous pouvez utiliser Data Quality Services (DQS) pour faire correspondre des données avant de les charger dans MDS. Cela évite la duplication des données dans MDS.  
  
> [!IMPORTANT]  
>  Vous pouvez continuer à utiliser la version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 du complément Master Data Services pour Excel après la mise à niveau de Master Data Services et de Data Quality Services vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2. Toutefois, aucune version antérieure du complément Master Data Services pour Excel ne fonctionnera après la mise à niveau vers SQL Server 2014 CTP2. Vous pouvez télécharger la version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 du complément Master Data Services pour Excel [ici](https://go.microsoft.com/fwlink/?LinkId=328664).  
  
## <a name="terms"></a>Termes  
 Si vous utilisez le complément, vous devez connaître les termes suivants.  
  
-   Le *référentiel MDS* est l'emplacement où toutes les données de référence sont stockées. Il s'agit d'une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configurée pour stocker des données MDS. Pour manipuler des données à partir du référentiel, vous devez les charger dans Excel, puis quand vous avez terminé votre travail, vous pouvez publier vos modifications dans le référentiel. Les administrateurs peuvent ajouter de nouvelles entités et de nouveaux attributs au référentiel.  
  
-   Les données*gérées par MDS* sont les données stockées dans le référentiel MDS que vous chargez dans Excel, les données étant affichées sous la forme de lignes en surbrillance. Vous pouvez ajouter des données non managées MDS à votre feuille de calcul, dans ce cas, celles-ci ne seront pas concernées par l'actualisation des données managées MDS.  
  
-   Un *modèle* est un conteneur de données. Plusieurs versions de ces conteneurs peuvent être créées, généralement la dernière version est aussi la plus récente. Pour plus d’informations, consultez [Modèles &#40;Master Data Services&#41;](../models-master-data-services.md).  
  
-   Une *entité* est une liste de données. Vous pouvez considérer une entité comme une table d'une base de données. Par exemple, l'entité **Couleur** peut contenir une liste de couleurs. Pour plus d’informations, consultez [Entités &#40;Master Data Services&#41;](../entities-master-data-services.md).  
  
-   Un *member* est une ligne de données. Chaque entité contient des membres. Un membre est **Bleu**. Pour plus d’informations, consultez [Membres &#40;Master Data Services&#41;](../members-master-data-services.md).  
  
-   Un *attribut* est une colonne de données. Chaque membre possède des attributs. Par exemple, l’attribut de **code** pour le membre **bleu** est **B**. Pour plus d’informations sur les attributs, consultez [attributs &#40;Master Data Services&#41;](../attributes-master-data-services.md).  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Créez une connexion à un référentiel [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .|[Se connecter à un référentiel MDS &#40;Complément MDS pour Excel&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md)|  
|Chargez les données managées MDS dans Excel.|[Charger des données MDS dans Excel](export-data-to-excel-from-master-data-services.md)|  
|Enregistrez une requête de raccourci que vous pouvez utiliser à l'avenir pour ouvrir les données managées MDS actuellement affichées.|[Enregistrer un fichier de requête de raccourci &#40;Complément MDS pour Excel#41;](save-a-shortcut-query-file-mds-add-in-for-excel.md)|  
|Partager des raccourcis avec d'autres utilisateurs.|[Envoyer par e-mail un fichier de requête de raccourci &#40;Complément MDS pour Excel#41;](email-a-shortcut-query-file-mds-add-in-for-excel.md)|  
|Afficher toutes les modifications apportées à un membre.|[Afficher toutes les annotations ou transactions pour un membre &#40;Complément MDS pour Excel&#41;](view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md)|  
|Avant de publier de nouvelles données, vérifier si certaines sont dupliquées.|[Mettre en correspondance les données similaires &#40;Complément MDS pour Excel&#41;](match-similar-data-mds-add-in-for-excel.md)|  
|Publier les données d'une feuille de calcul dans le référentiel MDS.|[Publier des données d’Excel dans MDS &#40;Complément MDS pour Excel&#41;](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)|  
|Créer une nouvelle entité avec les données dans la feuille de calcul. (Administrateurs uniquement.)|[Créer une entité &#40;Complément MDS pour Excel&#41;](create-an-entity-mds-add-in-for-excel.md)|  
|Créez un attribut basé sur un domaine, également appelé une liste contrainte. (Administrateurs uniquement.)|[Créer un attribut basé sur un domaine &#40;complément MDS pour Excel&#41;](create-a-domain-based-attribute-mds-add-in-for-excel.md)|  
|Définissez les propriétés de chargement et de publication des données dans le complément Master Data Services pour Excel. (Administrateurs uniquement.)|[Définition des propriétés pour le complément Master Data Services pour Excel](setting-properties-for-master-data-services-add-in-for-excel.md)|  
  
## <a name="related-content"></a>Contenu associé  
  
-   [Connexions &#40;Complément MDS pour Excel#41;](connections-mds-add-in-for-excel.md)  
  
-   [Chargement de données &#40;Complément MDS pour Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
-   [Fichiers de requête de raccourci &#40;Complément MDS pour Excel&#41;](shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [Mise en correspondance de la qualité des données dans le complément MDS pour Excel](data-quality-matching-in-the-mds-add-in-for-excel.md)  
  
-   [Publication des Complément MDS pour Excel de &#40;de données&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
-   [Génération d’un modèle &#40;Complément MDS pour Excel&#41;](building-a-model-mds-add-in-for-excel.md)  
  
-   [Sécurité &#40;Master Data Services&#41;](../security-master-data-services.md)  
  
  
