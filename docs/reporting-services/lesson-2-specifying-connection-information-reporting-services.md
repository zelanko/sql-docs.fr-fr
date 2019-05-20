---
title: 'Leçon 2 : Spécification des informations de connexion (Reporting Services) | Microsoft Docs'
ms.date: 05/01/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: 54405a3a-d7fa-4d95-8963-9aa224e5901e
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0a0c21b2662fc14977c4ac57687754d15d544994
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65106055"
---
# <a name="lesson-2-specifying-connection-information-reporting-services"></a>Leçon 2 : Spécification des informations de connexion (Reporting Services)

Dans la leçon 1, vous avez ajouté un rapport paginé [!INCLUDE[ssrsnoversion-md](../includes/ssrsnoversion-md.md)] à votre projet Tutorial.
  
Dans cette leçon, vous allez définir une *source de données*, des informations de connexion utilisées par le rapport pour accéder aux données d’une base de données relationnelle ou d’autres sources.

Pour ce rapport, vous allez ajouter l’exemple de base de données AdventureWorks2016 comme source de données. Ce tutoriel part du principe que cette base de données est située dans l’instance par défaut du [!INCLUDE[ssDE](../includes/ssde-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et installée sur votre ordinateur local.  

## <a name="to-set-up-a-connection"></a>Pour configurer une connexion  

1. Dans le volet **Données du rapport**, sélectionnez **Nouveau** > **Source de données**. Si le volet **Données du rapport** n’est pas visible, sélectionnez le menu **Affichage** > **Données du rapport**.

    ![ssrs-table-tutorial-2-new-data-source](media/ssrs-table-tutorial-2-new-data-source.png)

    La boîte de dialogue **Propriétés de la source de données** s’ouvre avec la section **Général** affichée.

    ![Boîte de dialogue Propriétés de la source de données](media/lesson-2-specifying-connection-information-reporting-services/vs-datasource-connection-properties-dialog-box.png)

2. Dans la zone de texte **Nom**, tapez « AdventureWorks2016 ».

3. Sélectionnez la case d’option **Connexion incorporée**.

4. Dans la zone de liste déroulante de sélection **Type**, sélectionnez « Microsoft SQL Server ».
  
5. Dans la zone de texte **Chaîne de connexion**, tapez la chaîne suivante :

    `Data source=localhost; initial catalog=AdventureWorks2016`

    > [!NOTE]
    > Cette chaîne de connexion part du principe que [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], le serveur de rapports et la base de données AdventureWorks2016 sont tous installés sur l’ordinateur local.
    >
    >Si ce n’est pas le cas, modifiez la chaîne de connexion et remplacez « localhost » par le nom de votre instance/serveur de base de données. Si vous utilisez [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] ou une instance nommée de SQL Server, vous devez modifier votre chaîne de connexion afin d’inclure les informations sur l’instance. Par exemple :
    >
    > `Data source=localhost\SQLEXPRESS; initial catalog=AdventureWorks2016`
    >
    > Pour plus d’informations sur les chaînes de connexion, consultez la section `See also` ci-dessous.

6. Sélectionnez l’onglet **Informations d’identification** et, sous la section **Modifiez les informations d’identification utilisées pour se connecter à la source de données**, sélectionnez la case d’option **Utiliser l’authentification Windows (sécurité intégrée)**.

7. Sélectionnez **OK** pour terminer le processus.

Le Concepteur de rapports ajoute la source de données AdventureWorks2016 au volet **Données du rapport**.

![ssrs-adventureworks-datasource](media/lesson-2-specifying-connection-information-reporting-services/ssrs-adventureworks-datasource2016.png)

## <a name="next-steps"></a>Étapes suivantes

Dans cette leçon, vous avez défini une connexion à l’exemple de base de données AdventureWorks2016. Poursuivez avec la [Leçon 3 : Définition d’un dataset pour le rapport de table &#40;Reporting Services&#41;](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md) afin de définir un dataset pour le rapport.

## <a name="see-also"></a>Voir aussi

[Connexions de données, sources de données et chaînes de connexion dans Reporting Services](report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)
