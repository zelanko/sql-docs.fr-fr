---
title: 'Leçon 1 : Créer un projet et un package de base avec SSIS | Microsoft Docs'
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 84d0b877-603f-4f8e-bb6b-671558ade5c2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ff31579a425f9e86fed11811c9d0a42c3113ee15
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75257072"
---
# <a name="lesson-1-create-a-project-and-basic-package-with-ssis"></a>Leçon 1 : Créer un projet et un package de base avec SSIS

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Au cours de cette leçon, vous créez un package ETL simple qui extrait des données d’une seule source de fichier plat, transforme ces données en utilisant deux transformations de recherche et écrit les données transformées dans une copie de la table de faits **FactCurrencyRate** de l’exemple de base de données **AdventureWorksDW2012**. Dans le cadre de cette leçon, vous apprenez à créer des packages, ajouter et configurer des sources de données et des destinations et enfin, à utiliser le nouveau flux de contrôle et les composants de flux de données.  
  
Avant de créer un package, vous devez comprendre le formatage utilisé pour les données sources et la destination. Vous êtes ensuite prêt à définir les transformations nécessaires pour mapper les données source avec les données de destination.  

## <a name="prerequisites"></a>Conditions préalables requises

Ce tutoriel s’appuie sur Microsoft SQL Server Data Tools, ensemble d’exemples de package, et sur un exemple de base de données.

* Pour installer SQL Server Data Tools, consultez [Télécharger SQL Server Data Tools](../ssdt/download-sql-server-data-tools-ssdt.md).  
  
* Pour télécharger tous les packages de leçons de ce tutoriel :

    1.  Accédez aux [fichiers du tutoriel Integration Services](https://www.microsoft.com/download/details.aspx?id=56827).

    2.  Sélectionnez le bouton **Télécharger**.

    3.  Sélectionnez le fichier **Creating a Simple ETL Package.zip**, puis sélectionnez **Suivant**.

    4.  Une fois le fichier téléchargé, décompressez son contenu dans un répertoire local.  

* Pour installer et déployer l’exemple de base de données **AdventureWorksDW2012**, consultez [Installer et configurer l’exemple de base de données AdventureWorks - SQL](../samples/adventureworks-install-configure.md).
  
## <a name="look-at-the-source-data"></a>Examiner la source de données
Dans le cadre de ce tutoriel, les données sources sont représentées par un ensemble de données monétaires d’historique dans un fichier plat nommé **SampleCurrencyData.txt**. Les données sources contiennent les quatre colonnes suivantes : le taux moyen de la devise, une clé de devise, une clé de date et le taux de clôture.  
  
Voici un exemple des données sources du fichier SampleCurrencyData.txt :  
  
<pre>1.00070049USD9/3/05 0:001.001201442  
1.00020004USD9/4/05 0:001  
1.00020004USD9/5/05 0:001.001201442  
1.00020004USD9/6/05 0:001  
1.00020004USD9/7/05 0:001.00070049  
1.00070049USD9/8/05 0:000.99980004  
1.00070049USD9/9/05 0:001.001502253  
1.00070049USD9/10/05 0:000.99990001  
1.00020004USD9/11/05 0:001.001101211  
1.00020004USD9/12/05 0:000.99970009</pre>  
  
Pour bien utiliser des données sources issues d’un fichier plat, il est important de comprendre comment le gestionnaire de connexions de fichiers plats interprète les données du fichier plat. Si la source du fichier plat est au format Unicode, le gestionnaire de connexions de fichiers plats définit toutes les colonnes avec le type [DT_WSTR] et une largeur par défaut égale à 50. Si la source du fichier plat est au format ANSI, les colonnes sont définies avec le type [DT_STR] et une largeur par défaut égale à 50. Il est probable que vous deviez changer ces valeurs par défaut pour affecter aux colonnes des types String qui s’appliquent davantage à vos données. Vous devez examiner le type de données de la destination, puis choisir ce type dans le gestionnaire de connexions de fichiers plats.  
  
## <a name="look-at-the-destination-data"></a>Examiner les données de destination
La destination des données sources est la copie de la table de faits **FactCurrencyRate** dans **AdventureWorksDW**. La table de faits **FactCurrencyRate** contient quatre colonnes et des relations avec deux tables de dimension, comme illustré ci-après.  
  
|Nom de la colonne|Type de données|Table de recherche|colonne de recherche|  
|---------------|-------------|----------------|-----------------|  
|AverageRate|float|None|None|  
|CurrencyKey|int (FK)|DimCurrency|CurrencyKey (PK)|  
|DateKey|int (FK)|DimDate|DateKey (PK)|  
|EndOfDayRate|float|None|None|  
  
## <a name="map-the-source-data-to-the-destination"></a>Mapper les données sources à la destination  
Notre analyse du format des données sources et de destination indique que des recherches sont nécessaires pour les valeurs **CurrencyKey** et **DateKey**. Les transformations qui effectuent ces recherches obtiennent ces valeurs en utilisant les autres clés des tables de dimension **DimCurrency** et **DimDate**.  
  
|Colonne de fichier plat|Nom de la table|Nom de la colonne|Type de données|  
|--------------------|--------------|---------------|-------------|  
|0|FactCurrencyRate|AverageRate|float|  
|1|DimCurrency|CurrencyAlternateKey|nchar (3)|  
|2|DimDate|FullDateAlternateKey|Date|  
|3|FactCurrencyRate|EndOfDayRate|float|  
  
## <a name="lesson-tasks"></a>Tâches de la leçon  
Cette leçon contient les tâches suivantes :  
  
-   [Étape 1 : Créer un projet Integration Services](../integration-services/lesson-1-1-creating-a-new-integration-services-project.md)  
  
-   [Étape 2 : Ajouter et configurer un gestionnaire de connexions de fichiers plats](../integration-services/lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
-   [Étape 3 : Ajouter et configurer un gestionnaire de connexions OLE DB](../integration-services/lesson-1-3-adding-and-configuring-an-ole-db-connection-manager.md)  
  
-   [Étape 4 : Ajouter une tâche de flux de données au package](../integration-services/lesson-1-4-adding-a-data-flow-task-to-the-package.md)  
  
-   [Étape 5 : Ajouter et configurer la source du fichier plat](../integration-services/lesson-1-5-adding-and-configuring-the-flat-file-source.md)  
  
-   [Étape 6 : Ajouter et configurer les transformations de recherche](../integration-services/lesson-1-6-adding-and-configuring-the-lookup-transformations.md)  
  
-   [Étape 7 : Ajouter et configurer la destination OLE DB](../integration-services/lesson-1-7-adding-and-configuring-the-ole-db-destination.md)  
  
-   [Étape 8 : Annoter et formater le package de la leçon 1](../integration-services/lesson-1-8-making-the-lesson-1-package-easier-to-understand.md)  
  
-   [Étape 9 : Tester le package de la leçon 1](../integration-services/lesson-1-9-testing-the-lesson-1-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Démarrer la leçon  
[Étape 1 : Créer un projet Integration Services](../integration-services/lesson-1-1-creating-a-new-integration-services-project.md)  
  
