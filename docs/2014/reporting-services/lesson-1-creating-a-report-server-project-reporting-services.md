---
title: 'Leçon 1 : Création d’un projet de serveur de rapports (Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 675671ca-e6c9-48a2-82e9-386778f3a49f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 52050b9513de2638cacc394309f7e87d6ba77709
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56032360"
---
# <a name="lesson-1-creating-a-report-server-project-reporting-services"></a>Leçon 1 : Création d’un projet de serveur de rapports (Reporting Services)
  Pour créer un rapport dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], vous devez commencer par créer un projet Report Server dans lequel vous allez enregistrer votre fichier de définition de rapport (.rdl), ainsi que les autres fichiers de ressources dont vous avez besoin pour votre rapport. Puis, vous créez le fichier réel de définition du rapport, et définissez une source de données pour votre rapport, un dataset et la mise en page du rapport. Quand vous exécutez le rapport, les données réelles sont extraites et combinées avec la mise en page, puis restituées sur votre écran, à partir duquel vous pouvez les exporter, les imprimer ou les enregistrer.  
  
 Dans cette leçon, vous allez apprendre à créer un projet Report Server dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Un projet Report Server permet de créer des rapports qui s'exécutent sur un serveur de rapports.  
  
### <a name="to-create-a-report-server-project"></a>Pour créer un projet Report Server  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)], puis cliquez sur **SQL Server Data Tools**. Si c’est la première fois que vous avez ouvert [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur **paramètres Business Intelligence** pour les paramètres d’environnement par défaut.  
  
2.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Dans la liste **Modèles installés** , cliquez sur **Business Intelligence**.  
  
4.  Cliquez sur **projet de serveur de rapports**.  
  
5.  Dans la zone **Nom**, tapez **Didacticiel**.  
  
6.  Cliquez sur **OK** pour créer le projet.  
  
     Le projet Didacticiel s'affiche dans l'Explorateur de solutions.  
  
### <a name="to-create-a-new-report-definition-file"></a>Pour créer un nouveau fichier de définition de rapport  
  
1.  Dans l’Explorateur de solutions, cliquez sur **rapports**, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
    > [!NOTE]  
    >  Si la fenêtre **Explorateur de solutions** n’est pas visible, dans le menu **Affichage** , cliquez sur **Explorateur de solutions**.  
  
2.  Dans le **ajouter un nouvel élément** boîte de dialogue **modèles**, cliquez sur **rapport**.  
  
3.  Dans la zone **Nom**, tapez **Sales Orders.rdl** , puis cliquez sur **Ajouter**.  
  
     Le Concepteur de rapports s'ouvre et affiche le nouveau fichier .rdl en mode Conception.  
  
 Le Concepteur de rapports est un composant [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] qui s'exécute dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Il dispose de deux vues : **Conception** et **aperçu**. Cliquez sur chacun des onglets pour passer d'une vue à une autre.  
  
 Vous définissez vos données dans le volet **Données du rapport** . Vous définissez la mise en page de votre rapport en mode **Conception** . Vous pouvez exécuter le rapport et visualiser son aspect en mode **Aperçu** .  
  
## <a name="next-task"></a>Tâche suivante  
 Vous avez créé avec succès un projet de rapport appelé « Didacticiel » et ajouté un fichier de définition de rapport (.rdl) au projet de rapport. Vous allez ensuite spécifier la source de données à utiliser pour le rapport. Consultez [leçon 2 : Spécification des informations de connexion &#40;Reporting Services&#41;](lesson-2-specifying-connection-information-reporting-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un rapport de tableau de base &#40;Didacticiel SSRS&#41;](create-a-basic-table-report-ssrs-tutorial.md)  
  
  
