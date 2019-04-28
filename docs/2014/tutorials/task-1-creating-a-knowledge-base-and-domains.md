---
title: 'Tâche 1 : Création d’une Base de connaissances et domaines | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 7d74a60b-8933-4038-bcbb-4e9dcc4f70e9
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: eeaebadd43fe1969ae1c728f8e2f8284ddf7f7ac
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822183"
---
# <a name="task-1-creating-a-knowledge-base-and-domains"></a>Tâche 1 : Création d’une base de connaissances et de domaines
  Dans cette tâche, vous allez créer le **fournisseurs** base de connaissances et créer des domaines qui est utilisé pour la correspondance des données et de nettoyage des données pour supprimer les doublons.  
  
1.  Lancez **Data Quality Client**. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2012**, cliquez sur **Data Quality Services**, puis cliquez sur  **Data Quality Client**.  
  
2.  Dans le **se connecter au serveur** boîte de dialogue, sélectionnez l’instance de serveur de base de données sur lequel DQS est installée, puis cliquez sur **Connect**.  
  
     ![Se connecter à la boîte de dialogue serveur](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-01.jpg "se connecter à la boîte de dialogue serveur")  
  
3.  Dans le Client de qualité des données de page d’accueil, dans le **gestion de la Base de connaissances** volet, cliquez sur **nouvelle Base de connaissances**.  
  
     ![Gestion de la Base de connaissances - nouvelle base de connaissances](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-02.jpg "gestion de la Base de connaissances - nouvelle base de connaissances")  
  
4.  Entrez **fournisseurs** pour **nom** de la base de connaissances.  
  
     ![Nouvelle Base de connaissances - gestion des domaines](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-03.jpg "nouvelle Base de connaissances - gestion des domaines")  
  
5.  Vérifiez que **créer la Base de connaissances à partir de** champ est défini sur **aucun** dans la mesure où vous créez le **fournisseurs** base de connaissances à partir de zéro.  
  
6.  Vérifiez que **gestion des domaines** est sélectionné pour le **activité** et cliquez sur **suivant**. L'activité de Gestion de l'arborescence du domaine vous permet de créer et gérer des domaines dans la base de connaissances.  
  
7.  Dans le **gestion des domaines** fenêtre, cliquez sur **créer un domaine** bouton de barre d’outils pour créer un domaine.  
  
     ![Créer le bouton de barre d’outils de domaine](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-04.jpg "créer le bouton de barre d’outils de domaine")  
  
8.  Dans le **créer un domaine** boîte de dialogue, tapez **ID du fournisseur** pour le **nom de domaine**, puis cliquez sur **OK**.  
  
     ![Créer la boîte de dialogue domaine](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-05.jpg "créer la boîte de dialogue domaine")  
  
9. Répétez l'étape précédente pour créer les domaines suivants avec les paramètres par défaut. Pour simplifier le didacticiel, vous définissez le **Type de données** de tous les domaines en tant que **chaîne**. Les autres types de données autorisés sont : Entier, décimal et Date. Lorsque le **utiliser des valeurs Menantes** option est activée (par défaut), tous les synonymes sont remplacés par la valeur de début du groupe de synonymes dans la sortie. Paramètre **normaliser la chaîne** option (valeur par défaut) supprime tous les caractères spéciaux dans les valeurs de domaine. Le **Format de sortie à** option vous permet de sélectionner la mise en forme est appliquée lorsque les valeurs de données dans le domaine sont générées. Sélectionnez **activer le vérificateur d’orthographe** (valeur par défaut) pour exécuter le vérificateur orthographique sur toutes les valeurs de chaîne en remplissant le domaine. Le **langage** paramètre spécifie la version linguistique de la **le vérificateur d’orthographe** vous souhaitez appliquer. Sélectionnez **désactiver les algorithmes d’erreur de syntaxe** pour remplir le domaine sans vérifier les valeurs de chaîne pour les erreurs de syntaxe. Consultez [créer un domaine](https://msdn.microsoft.com/library/hh510401.aspx) rubrique dans la bibliothèque MSDN pour plus d’informations.  
  
    -   Nom du fournisseur  
  
    -   Adresse de messagerie  
  
    -   Adresse  
  
    -   Ville  
  
    -   État  
  
    -   Pays  
  
    -   Code postal  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 2 : Ajout de valeurs de domaine manuellement](../../2014/tutorials/task-2-adding-domain-values-manually.md)  
  
  
