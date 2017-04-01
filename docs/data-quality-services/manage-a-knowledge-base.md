---
title: "G&#233;rer une base de connaissances | Microsoft Docs"
ms.custom: ""
ms.date: "06/04/2013"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 27f306f4-d67c-47f5-b35c-4260cc5d36e3
caps.latest.revision: 9
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 9
---
# G&#233;rer une base de connaissances
  Cette rubrique décrit comment remplir les fonctions de gestion sur une base de connaissances dans [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Vous pouvez supprimer une base de connaissances, la déverrouiller, ignorer vos modifications, la renommer et afficher ses propriétés.  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a> Conditions préalables  
 Pour gérer une base de connaissances, la base de connaissances doit avoir été déjà créée, et publiée (si une autre personne l'a créée) ou fermée (si vous l'avez créée).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Vous devez disposer du rôle dqs_kb_editor ou dqs_administrator sur la base de données DQS_MAIN pour ouvrir une base de connaissances.  
  
##  <a name="Manage"></a> Gérer une base de connaissances  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Exécutez l’Application Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Dans l'écran d'accueil de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , cliquez sur **Ouvrir une base de connaissances**.  
  
3.  Cliquez avec le bouton droit sur une base de connaissances dans la table des bases de connaissances.  
  
4.  Dans le menu contextuel, vous pouvez effectuer les tâches suivantes :  
  
    1.  **Ouvrez**: cliquez pour ouvrir la base de connaissances dans l’activité sélectionnée dans le **Sélectionner une activité** volet.  
  
    2.  **Déverrouiller**: vous pouvez déverrouiller la base de connaissances si vous êtes l’utilisateur qui travaillait sur la base de connaissances dans une des étapes de gestion de domaine, découverte des connaissances et l’activité de stratégie de correspondance et fermé. Si vous déchargez la base de connaissances, une autre personne peut l'ouvrir et travailler dessus. Cette commande n'est pas disponible si la base de connaissances n'est pas dans un état d'une activité. Pour plus d’informations, consultez [Ouvrir une Base de connaissances](../data-quality-services/open-a-knowledge-base.md).  
  
    3.  **Ignorer le travail**: lorsque la base de connaissances est dans un état de travail, comme indiqué par une entrée dans le champ État de la table. Cette commande n'est pas disponible si la base de connaissances n'est pas dans un état d'une activité ou si la base de connaissances est verrouillée. Pour plus d’informations, consultez [Ouvrir une Base de connaissances](../data-quality-services/open-a-knowledge-base.md).  
  
    4.  **Renommer**: cliquez pour modifier le champ de la Base de connaissances de la table de la base de connaissances que vous avez cliqué sur. Modifiez le nom, puis cliquez sur cette base de connaissances et sur une autre dans le champ pour accepter le changement de nom.  
  
    5.  **Supprimer**: cliquez pour supprimer la base de connaissances de la base de données DQS_MAIN sur [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].  
  
    6.  **Propriétés**: cliquez pour afficher les propriétés de la base de données en lecture seule.  
  
        1.  **Source de Base de connaissances**: la base de connaissances basé sur cette base de données. Ce paramètre est facultatif.  
  
        2.  **État**: indique si la base de connaissances est **de travail** et si elle est dans une activité de gestion des connaissances spécifiques, comme déterminé lors de la dernière fermeture. L’état peut être **de travail**, dans lequel la base de connaissances est ouverte dans une session de gestion des connaissances, mais pas dans une activité spécifique, ou **en cours** plus une activité de gestion des connaissances, dans lequel la base de connaissances est ouverte dans une session de gestion des connaissances et dans une activité spécifique.  
  
        3.  **Est verrouillé**: **True** Si la base de connaissances a été verrouillée, **False** Si ce n’est pas  
  
        4.  **Contenu non publié**: True si la base de connaissances contient des données qui le n'a pas été enregistrée par publication, False dans le cas contraire  
  
        5.  **Verrouillé par**: le nom de l’utilisateur qui a fermé la base de connaissances verrouillée  
  
        6.  **Verrouillé**: date du verrouillage  
  
        7.  **Créé par**: le nom de l’utilisateur qui a créé la base de connaissances, avec le réseau auquel il appartient  
  
        8.  **Date de création**: date de création  
  
##  <a name="FollowUp"></a> Suivi : après la gestion d'une base de connaissances  
 Après que vous avez géré une base de connaissances, l'étape suivante varie selon l'action effectuée sur la base de connaissances :  
  
-   Si vous avez ouvert la base de connaissances, vous continuerez dans l'activité que vous avez sélectionnée.  
  
-   Si vous l'avez déverrouillée, elle est disponible pour qu'une autre personne l'ouvre et travaille dessus, dans l'état indiqué.  
  
-   Si vous aviez ignoré le travail sur la base de connaissances, celle-ci sera disponible dans son dernier état publié.  
  
-   Si vous l'avez renommée, vous devez ouvrir la base de connaissances renommée pour travailler dessus.  
  
-   Si vous la supprimez, vous devrez sélectionner une autre base de connaissances sur laquelle travailler ou en créez une nouvelle.  
  
  