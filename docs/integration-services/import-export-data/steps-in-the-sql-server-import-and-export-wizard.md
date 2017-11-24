---
title: "Les étapes dans le SQL Server Assistant Importation et exportation | Documents Microsoft"
ms.custom: 
ms.date: 02/16/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: import-export-data
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 816fb1bd-7bb9-450d-ad65-e4c2d02eaff8
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 22d1f4b78fadab6d7b6659104b54a564f11da308
ms.contentlocale: fr-fr
ms.lasthandoff: 09/27/2017

---
# <a name="steps-in-the-sql-server-import-and-export-wizard"></a>Étapes dans SQL Server Assistant Importation et exportation
Cette rubrique décrit la séquence d’étapes pour l’importation et exportation de données avec le SQL Server Assistant Importation et exportation. Il contient également des liens vers les différentes pages de documentation qui décrivent chaque page ou de la boîte de dialogue que s’affiche dans l’Assistant.

Cette rubrique décrit uniquement les **étapes** dans l’Assistant. Si vous avez besoin d’un autre élément, consultez [les tâches et contenu](#related).

## <a name="steps-for-importing-and-exporting-data"></a>Étapes pour l’importation et exportation de données  
 Le tableau suivant répertorie les étapes liées à l’importation et à l’exportation des données et les pages correspondantes de l’Assistant. Selon les options que vous sélectionnez dans l’Assistant, vous n’en général, consultez toutes ces pages.  

Pour examiner rapidement les plusieurs écrans qui s’affichent dans une session normale, examinez cet exemple de bout en bout simple sur une seule page - [prise en main avec cet exemple simple de l’Assistant Importation et exportation](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md).

|Étape|Pages de l’assistant|  
|----------|------------------|  
|**Bienvenue**<br />Vous n’avez aucune action à effectuer dans cette page.|[Assistant Importation et Exportation SQL Server](../../integration-services/import-export-data/welcome-to-sql-server-import-and-export-wizard.md)|  
|**Choisissez la source** des données.|[Choisissez une Source de données](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)|  
|**Choisissez la destination** des données.|[Choisir une Destination](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)|  
|**Configurer la destination**. (étapes facultatives)<br /><br /> -   Créez une base de données de destination.<br />-   Si vous copiez des données dans un fichier texte, configurer des paramètres supplémentaires.|[Créer la base de données](../../integration-services/import-export-data/create-database-sql-server-import-and-export-wizard.md)<br /><br />[Configurer la Destination de fichier plat](../../integration-services/import-export-data/configure-flat-file-destination-sql-server-import-and-export-wizard.md)|  
|**Spécifiez ce que vous souhaitez copier.**|[Spécifier la copie de la Table ou la requête](../../integration-services/import-export-data/specify-table-copy-or-query-sql-server-import-and-export-wizard.md)<br /><br />[Sélectionner les Tables sources et des vues](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md)<br /><br />[Fournir une requête Source](../../integration-services/import-export-data/provide-a-source-query-sql-server-import-and-export-wizard.md)|  
|**Configurer l’opération de copie**. (étapes facultatives)<br /><br /> -   Créer une table de destination.<br />-Décider quoi faire si l’Assistant ne sait pas comment mapper des types de données entre la source et de destination que vous avez sélectionné.<br />-   Passer en revue les mappages de colonnes entre la source et de destination.<br />-   Gérer les problèmes de conversion de types de données entre la source et la destination.<br />-   Afficher un aperçu des données à copier.|[Créer l’instruction SQL Table](../../integration-services/import-export-data/create-table-sql-statement-sql-server-import-and-export-wizard.md)<br /><br />[Convertir les Types sans vérification de la Conversion](../../integration-services/import-export-data/convert-types-without-conversion-checking-sql-server-import-and-export-wizard.md)<br /><br />[Mappages de colonnes](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md)<br /><br />[Passez en revue le mappage de Type de données](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md)<br /><br />[Boîte de dialogue de détails de Conversion de colonne](../../integration-services/import-export-data/column-conversion-details-dialog-box-sql-server-import-and-export-wizard.md)<br /><br />[Boîte de dialogue Aperçu données](../../integration-services/import-export-data/preview-data-dialog-box-sql-server-import-and-export-wizard.md)|  
|**Copier les données.**<br /><br /> Si vous le souhaitez, enregistrez vos paramètres sous forme de package SQL Server Integration Services (SSIS).|[Enregistrez et exécutez le Package](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md)<br /><br />[Enregistrer le package SSIS](../../integration-services/import-export-data/save-ssis-package-sql-server-import-and-export-wizard.md)<br /><br />[Terminez l’Assistant](../../integration-services/import-export-data/complete-the-wizard-sql-server-import-and-export-wizard.md)<br /><br />[Opération](../../integration-services/import-export-data/performing-operation-sql-server-import-and-export-wizard.md)|  

> [!TIP]
> Pour afficher la documentation sur une page ou une boîte de dialogue déterminée de l’Assistant, appuyez sur la touche F1 à partir de cette page.

## <a name="related"></a>Contenu et des tâches connexes  
Voici quelques autres tâches de base.
-   **Voir un exemple rapide du fonctionne de l’Assistant.**

    -   **Si vous préférez afficher les captures d’écran.** Examinez cet exemple de bout en bout simple sur une seule page - [prise en main avec cet exemple simple de l’Assistant Importation et exportation](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md).

    -   **Si vous préférez regarder une vidéo.** Regardez cette vidéo de quatre minutes à partir de YouTube qui montre l’Assistant et explique clairement et simplement comment exporter des données vers Excel - [à l’aide du SQL Server Assistant Importation et exportation pour l’exportation vers Excel](https://go.microsoft.com/fwlink/?linkid=829049).

-   **En savoir plus sur le fonctionne de l’Assistant.**

    -   **En savoir plus sur l’Assistant.** Si vous recherchez une vue d’ensemble de l’Assistant, consultez [Importer et exporter des données avec l’Assistant Importation et Exportation SQL Server](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).

    -   **Découvrez comment se connecter à des destinations et des sources de données.** Si vous recherchez des informations sur la façon de se connecter à vos données, sélectionnez la page à partir de la liste ici - [se connecter aux sources de données avec le SQL Server Assistant Importation et exportation](../../integration-services/import-export-data/connect-to-data-sources-with-the-sql-server-import-and-export-wizard.md). Il existe une page distincte de la documentation pour chacun de plusieurs sources de données couramment utilisées. 

-   **Démarrer l’Assistant.** Si vous êtes prêt à exécuter l’Assistant et souhaitez simplement savoir comment le démarrer, consultez [Démarrer l’Assistant Importation et Exportation SQL Server](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md).

-     **Procurez-vous l’Assistant.** Si vous souhaitez exécuter l’Assistant, mais [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’est pas installé sur votre ordinateur, vous pouvez installer l’Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en installant SSDT (SQL Server Data Tools). Pour plus d’informations, consultez [Télécharger SSDT (SQL Server Data Tools)](https://msdn.microsoft.com/library/mt204009.aspx).



