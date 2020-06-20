---
title: Mettre fin à l’activité de gestion des domaines | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ab6505ad-3090-453b-bb01-58435e7fa7c0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 16e030b52e4c7f99368efd8054f87df495b67257
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84937710"
---
# <a name="end-the-domain-management-activity"></a>Terminer l'activité de gestion de l'arborescence du domaine
  Cette rubrique décrit comment effectuer, fermer ou annuler l'activité de gestion de l'arborescence du domaine dans [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). La gestion de l'arborescence du domaine n'étant pas exécutée par un Assistant, les contrôles décrits ci-dessous peuvent être utilisés à partir de toutes les pages de l'activité de gestion de l'arborescence du domaine.  
  
## <a name="end-domain-management"></a>Terminer la gestion de l'arborescence du domaine  
 **Terminer**  
 Cliquez sur cette option pour terminer la gestion de l'arborescence du domaine. Une fenêtre s'affichera pour vous permettre d'effectuer les opérations suivantes :  
  
-   **Oui. Publier la base de connaissances et quitter** : la base de connaissances sera publiée en vue de son utilisation par l’utilisateur actuel ou d’autres utilisateurs. La base de connaissances ne sera pas verrouillée, l'état de la base de connaissances (dans la table de bases de connaissances) sera défini sur Vide, et les activités de gestion de l'arborescence du domaine et de découverte des connaissances seront disponibles. L'écran Ouvrir la base de connaissances s'affichera à nouveau.  
  
-   **Non-enregistrer le travail dans la base de connaissances et quitter**: votre travail sera enregistré, la base de connaissances restera verrouillée et l’état de la base de connaissances sera défini sur en cours. Les activités de gestion de l'arborescence du domaine et de découverte des connaissances seront disponibles. La page d'accueil s'affichera à nouveau.  
  
-   **Annuler-rester sur l’écran actuel**: la fenêtre contextuelle est fermée et vous êtes redirigé vers l’écran de gestion de l’objet de domaine.  
  
 **Annuler**  
 Cliquez sur cette option pour terminer l'activité de gestion de l'arborescence du domaine, auquel cas vous perdrez votre travail, et revenir à la page d'accueil de DQS.  
  
 **Close**  
 Cliquez sur cette option pour enregistrer votre travail et revenir à la page d'accueil de DQS. La base de connaissances sera verrouillée, et l'état de la base de connaissances de la table de bases de connaissances dans l'écran **Ouvrir la base de connaissances** indiquera **Gestion de l'arborescence du domaine**. Après avoir cliqué sur **Fermer**, revenez à l'écran **Gestion de l'arborescence du domaine** pour effectuer l'activité de découverte des connaissances, cliquez sur **Terminer**, puis sur **Oui** pour publier la base de connaissances ou sur **Non** pour enregistrer le travail dans la base de connaissances et quitter.  Pour plus d'informations sur l'ouverture d'une base de connaissances verrouillée, consultez [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).  
  
  
