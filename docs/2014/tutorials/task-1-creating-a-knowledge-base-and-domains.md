---
title: 'Tâche 1 : création d’une base de connaissances et de domaines | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 7d74a60b-8933-4038-bcbb-4e9dcc4f70e9
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 79edd8566f2b3c9b586bc8c8815e1d9bc586fb05
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "65481247"
---
# <a name="task-1-creating-a-knowledge-base-and-domains"></a>Tâche 1 : Création d’une base de connaissances et de domaines
  Au cours de cette tâche, vous allez créer la base de connaissances **fournisseurs** et créer des domaines qui sont utilisés pour nettoyer les données et les données correspondantes pour supprimer les doublons.  
  
1.  Lancez **Data Quality client**. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2012**, sur **Data Quality Services**, puis sur **Data Quality client**.  
  
2.  Dans la boîte de dialogue **se connecter au serveur** , sélectionnez l’instance de serveur de base de données sur laquelle le DQS est installé, puis cliquez sur **se connecter**.  
  
     ![Boîte de dialogue se connecter au serveur](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-01.jpg "Boîte de dialogue Connexion au serveur")  
  
3.  Dans la page d’espace de Data Quality Client, dans le volet gestion de la **base de connaissances** , cliquez sur **nouvelle base de connaissances**.  
  
     ![Gestion des bases de connaissances - Nouvelle base de connaissances](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-02.jpg "Gestion des bases de connaissances - Nouvelle base de connaissances")  
  
4.  Entrez **Suppliers** pour le **nom** de la base de connaissances.  
  
     ![Nouvelle base de connaissances - Gestion du domaine](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-03.jpg "Nouvelle base de connaissances - Gestion du domaine")  
  
5.  Vérifiez que l’option **créer une base de connaissances à partir de** est définie sur **aucun** , car vous créez la base de connaissances **fournisseurs** à partir de zéro.  
  
6.  Vérifiez que **gestion de domaine** est sélectionné pour l' **activité** , puis cliquez sur **suivant**. L'activité de Gestion de l'arborescence du domaine vous permet de créer et gérer des domaines dans la base de connaissances.  
  
7.  Dans la fenêtre **gestion des domaines** , cliquez sur le bouton **créer un domaine** de la barre d’outils pour créer un domaine.  
  
     ![Bouton de la barre d'outils Créer un domaine](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-04.jpg "Bouton de la barre d'outils Créer un domaine")  
  
8.  Dans la boîte de dialogue **créer un domaine** , tapez **ID du fournisseur** pour le **nom de domaine**, puis cliquez sur **OK**.  
  
     ![Boîte de dialogue Créer une table](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-05.jpg "Boîte de dialogue Créer une table")  
  
9. Répétez l'étape précédente pour créer les domaines suivants avec les paramètres par défaut. Pour simplifier le didacticiel, vous définissez le **type de données** de tous les domaines en tant que **chaîne**. Les autres types de données autorisés sont : entier, décimal, et date. Lorsque l’option **utiliser des valeurs de début** est sélectionnée (valeur par défaut), tous les synonymes sont remplacés par la valeur de début du groupe de synonymes dans la sortie. La définition de l’option **normaliser la chaîne** (valeur par défaut) supprime tous les caractères spéciaux dans les valeurs de domaine. L’option **mettre en forme la sortie vers** vous permet de sélectionner la mise en forme qui est appliquée lorsque les valeurs de données dans le domaine sont générées. Sélectionnez **activer le vérificateur d’orthographe** (par défaut) pour exécuter le vérificateur d’orthographe sur toutes les valeurs de chaîne lors du remplissage du domaine. Le paramètre de **langue** spécifie la version linguistique du **vérificateur d’orthographe** que vous souhaitez appliquer. Sélectionnez **Désactiver les algorithmes d’erreur de syntaxe** pour remplir le domaine sans vérifier les valeurs de chaîne pour les erreurs de syntaxe. Pour plus d’informations, consultez la rubrique [créer un domaine](https://msdn.microsoft.com/library/hh510401.aspx) dans MSDN Library.  
  
    -   Nom du fournisseur  
  
    -   E-mail du contact  
  
    -   Adresse  
  
    -   City  
  
    -   State  
  
    -   Country  
  
    -   Zip  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 2 : Ajout de valeurs de domaine manuellement](../../2014/tutorials/task-2-adding-domain-values-manually.md)  
  
  
