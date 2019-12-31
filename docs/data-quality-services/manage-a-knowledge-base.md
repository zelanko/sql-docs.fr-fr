---
title: Gérer une base de connaissances
ms.date: 06/04/2013
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 27f306f4-d67c-47f5-b35c-4260cc5d36e3
author: swinarko
ms.author: sawinark
ms.openlocfilehash: 1fda81ac39233435dbcd0546e452878cc6767b33
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75247149"
---
# <a name="manage-a-knowledge-base"></a>Gérer une base de connaissances

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Cette rubrique décrit comment remplir les fonctions de gestion sur une base de connaissances dans [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Vous pouvez supprimer une base de connaissances, la déverrouiller, ignorer vos modifications, la renommer et afficher ses propriétés.  
  
##  <a name="BeforeYouBegin"></a>Avant de commencer  
  
###  <a name="Prerequisites"></a>Conditions préalables  
 Pour gérer une base de connaissances, la base de connaissances doit avoir été déjà créée, et publiée (si une autre personne l'a créée) ou fermée (si vous l'avez créée).  
  
###  <a name="Security"></a>Caution  
  
####  <a name="Permissions"></a>Autorisations  
 Vous devez disposer du rôle dqs_kb_editor ou dqs_administrator sur la base de données DQS_MAIN pour ouvrir une base de connaissances.  
  
##  <a name="Manage"></a>Gérer une base de connaissances  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Exécutez l’Application Data Quality client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Dans l'écran d'accueil de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , cliquez sur **Ouvrir une base de connaissances**.  
  
3.  Cliquez avec le bouton droit sur une base de connaissances dans la table des bases de connaissances.  
  
4.  Dans le menu contextuel, vous pouvez effectuer les tâches suivantes :  
  
    1.  **Ouvrir**: cliquez pour ouvrir la base de connaissances dans l’activité sélectionnée dans le volet **Sélectionner une activité** .  
  
    2.  **Déverrouiller**: vous pouvez déverrouiller la base de connaissances si vous êtes l’utilisateur qui travaillait sur la base de connaissances dans l’une des étapes de la gestion des domaines, de la découverte des connaissances et de l’activité de stratégie de correspondance, et que vous l’avez fermée. Si vous déchargez la base de connaissances, une autre personne peut l'ouvrir et travailler dessus. Cette commande n'est pas disponible si la base de connaissances n'est pas dans un état d'une activité. Pour plus d'informations, consultez [Open a Knowledge Base](../data-quality-services/open-a-knowledge-base.md).  
  
    3.  **Ignorer le travail**: cliquez sur lorsque la base de connaissances est dans un état de travail, comme indiqué par une entrée dans le champ État de la table. Cette commande n'est pas disponible si la base de connaissances n'est pas dans un état d'une activité ou si la base de connaissances est verrouillée. Pour plus d'informations, consultez [Open a Knowledge Base](../data-quality-services/open-a-knowledge-base.md).  
  
    4.  **Renommer**: cliquez pour que le champ de la base de connaissances de la table puisse être modifié pour la base de connaissances sur laquelle vous avez cliqué avec le bouton droit. Modifiez le nom, puis cliquez sur cette base de connaissances et sur une autre dans le champ pour accepter le changement de nom.  
  
    5.  **Supprimer**: cliquez pour supprimer la base de connaissances de la base de [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]données DQS_MAIN sur.  
  
    6.  **Propriétés**: cliquez sur cette propriété pour afficher les propriétés de la base de données en lecture seule.  
  
        1.  **Base de connaissances source**: base de connaissances sur laquelle cette base de données a été basée. Cette étape est facultative.  
  
        2.  **État**: indique si la base de connaissances est **en cours** et si elle se trouve dans une activité spécifique de gestion des connaissances, comme déterminé lors de sa dernière fermeture. L'état peut être **En cours**, à savoir que la base de connaissances est ouverte dans une session de gestion des connaissances, mais pas dans une activité spécifique, ou **En cours** plus une activité de gestion des connaissances, dans laquelle la base de connaissances est ouverte dans une session de gestion des connaissances, et dans une activité spécifique.  
  
        3.  **Est verrouillé**: **true** si la base de connaissances a été verrouillée, **false** dans le cas contraire  
  
        4.  **Contient du contenu non publié**: true si la base de connaissances contient du contenu qui n’a pas été enregistré par publication, false dans le cas contraire  
  
        5.  **Verrouillé par**: nom de l’utilisateur qui a fermé la base de connaissances, en la verrouillant  
  
        6.  **Date de verrouillage**: date de verrouillage  
  
        7.  **Créé par**: nom de l’utilisateur qui a créé la base de connaissances, avec le réseau auquel elle appartient  
  
        8.  **Date de création**: date de création  
  
##  <a name="FollowUp"></a>Suivi : après la gestion d’une base de connaissances  
 Après que vous avez géré une base de connaissances, l'étape suivante varie selon l'action effectuée sur la base de connaissances :  
  
-   Si vous avez ouvert la base de connaissances, vous continuerez dans l'activité que vous avez sélectionnée.  
  
-   Si vous l'avez déverrouillée, elle est disponible pour qu'une autre personne l'ouvre et travaille dessus, dans l'état indiqué.  
  
-   Si vous aviez ignoré le travail sur la base de connaissances, celle-ci sera disponible dans son dernier état publié.  
  
-   Si vous l'avez renommée, vous devez ouvrir la base de connaissances renommée pour travailler dessus.  
  
-   Si vous la supprimez, vous devrez sélectionner une autre base de connaissances sur laquelle travailler ou en créez une nouvelle.  
  
  
