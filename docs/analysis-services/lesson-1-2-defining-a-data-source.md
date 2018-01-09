---
title: "Définition d’une Source de données | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: 5a3e83c9-8788-431e-85b0-a68c79377ff3
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 3c1504d26e2c7cbdbdacf943e17d7514ba20b786
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="lesson-1-2---defining-a-data-source"></a>Leçon 1-2-définition d’une Source de données
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]Après avoir créé un [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] projet, vous commencez généralement avec le projet en définissant une ou plusieurs sources de données utilisées par le projet. Lorsque vous définissez une source de données, vous définissez les informations de la chaîne de connexion qui seront utilisées pour se connecter à la source de données. Pour plus d’informations, consultez [Créer une source de données &#40;SSAS Multidimensionnel&#41;](../analysis-services/multidimensional-models/create-a-data-source-ssas-multidimensional.md).  
  
Au cours de la tâche suivante, vous allez définir la base de données exemple AdventureWorksDWSQLServer2012 comme source de données pour le projet Didacticiel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Si cette base de données est située sur votre ordinateur local dans le cadre de ce didacticiel, sachez que les bases de données sources sont généralement hébergées sur un ou plusieurs ordinateurs distants.  
  
### <a name="to-define-a-new-data-source"></a>Pour définir une nouvelle source de données  
  
1.  Dans l’explorateur de solutions (à droite de la fenêtre de Microsoft Visual Studio), cliquez avec le bouton droit sur **Sources de données**, puis cliquez sur **Nouvelle vue de source de données**.  
  
2.  Sur le **Bienvenue dans l’Assistant Source de données** page de la **Assistant Source de données**, cliquez sur **suivant** pour ouvrir le **sélectionner la méthode de définition de la connexion** page.  
  
3.  Dans la page **Sélectionner la méthode de définition de la connexion**, vous pouvez définir une source de données basée sur une nouvelle connexion, sur une connexion existante ou sur un objet de source de données défini précédemment. Au cours de ce didacticiel, vous allez définir une source de données basée sur une nouvelle connexion. Vérifiez que l’option **Créer une source de données basée sur une connexion existante ou nouvelle** est sélectionnée, puis cliquez sur **Nouvelle**.  
  
4.  Dans la boîte de dialogue **Gestionnaire de connexions** vous définissez les propriétés de connexion de la source de données. Dans la zone de liste **Fournisseur** , vérifiez que **Native OLE DB\SQL Server Native Client 11.0** est sélectionné.  
  
    [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] prend également en charge d’autres fournisseurs, affichés dans la liste **Fournisseur** .  
  
5.  Dans la zone de texte **Nom du serveur** , tapez **localhost**.  
  
    Pour vous connecter à une instance nommée sur votre ordinateur local, tapez **localhost\\<instance name>**. Pour se connecter à l'ordinateur spécifique au lieu de l'ordinateur local, tapez le nom d'ordinateur ou l'adresse IP.  
  
6.  Vérifiez que l’option **Utiliser l’authentification Windows** est sélectionnée. Dans la liste **Sélectionner ou entrer un nom de base de données** , sélectionnez **AdventureWorksDW2012**.  
  
7.  Cliquez sur **Tester la connexion** pour tester la connexion à la base de données.  
  
8.  Cliquez sur **OK**, puis sur **Suivant**.  
  
9. Dans la page **Informations d’emprunt d’identité** de l’Assistant, vous pouvez définir les informations d’identification de sécurité que [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] doit utiliser pour se connecter à la source de données. L'emprunt d'identité affecte le compte Windows utilisé pour la connexion à la source de données lorsque l'authentification Windows est sélectionnée. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ne prend pas en charge l’emprunt d’identité pour le traitement des objets OLAP. Sélectionnez **Utiliser le compte de service**, puis cliquez sur **Suivant**.  
  
10. Dans la page **Fin de l’Assistant** , acceptez le nom par défaut **Adventure Works DW 2012**et cliquez sur **Terminer** pour créer la source de données.  
  
> [!NOTE]  
> Pour modifier les propriétés d’une source de données après qu’elle a été créée, double-cliquez sur cette source de données dans le dossier **Sources de données** pour en afficher les propriétés dans le **Concepteur de source de données**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
[Définition d'une vue de source de données](../analysis-services/lesson-1-3-defining-a-data-source-view.md)  
  
## <a name="see-also"></a>Voir aussi  
[Créer une source de données &#40;SSAS Multidimensionnel&#41;](../analysis-services/multidimensional-models/create-a-data-source-ssas-multidimensional.md)  
  
