---
title: End the Domain Management Activity | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ab6505ad-3090-453b-bb01-58435e7fa7c0
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c9f53d3878ec6f5eb9c0996d7162fed792bf4930
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2018
ms.locfileid: "51033366"
---
# <a name="end-the-domain-management-activity"></a>Terminer l'activité de gestion de l'arborescence du domaine
  Cette rubrique décrit comment effectuer, fermer ou annuler l'activité de gestion de l'arborescence du domaine dans [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). La gestion de l'arborescence du domaine n'étant pas exécutée par un Assistant, les contrôles décrits ci-dessous peuvent être utilisés à partir de toutes les pages de l'activité de gestion de l'arborescence du domaine.  
  
## <a name="end-domain-management"></a>Terminer la gestion de l'arborescence du domaine  
 **Terminer**  
 Cliquez sur cette option pour terminer la gestion de l'arborescence du domaine. Une fenêtre s'affichera pour vous permettre d'effectuer les opérations suivantes :  
  
-   **Oui. Publier la base de connaissances et quitter**: la base de connaissances sera publiée en vue de son utilisation par l'utilisateur actuel ou d'autres. La base de connaissances ne sera pas verrouillée, l'état de la base de connaissances (dans la table de bases de connaissances) sera défini sur Vide, et les activités de gestion de l'arborescence du domaine et de découverte des connaissances seront disponibles. L'écran Ouvrir la base de connaissances s'affichera à nouveau.  
  
-   **Non. Enregistrer le travail dans la base de connaissances et quitter**: votre travail sera enregistré, la base de connaissances restera verrouillée et l'état de la base de connaissances sera défini sur En cours. Les activités de gestion de l'arborescence du domaine et de découverte des connaissances seront disponibles. La page d'accueil s'affichera à nouveau.  
  
-   **Annuler. Rester sur l'écran actif**: la fenêtre sera fermée et l'écran de gestion de l'arborescence du domaine s'affichera à nouveau.  
  
 **Annuler**  
 Cliquez sur cette option pour terminer l'activité de gestion de l'arborescence du domaine, auquel cas vous perdrez votre travail, et revenir à la page d'accueil de DQS.  
  
 **Fermer**  
 Cliquez sur cette option pour enregistrer votre travail et revenir à la page d'accueil de DQS. La base de connaissances sera verrouillée, et l'état de la base de connaissances de la table de bases de connaissances dans l'écran **Ouvrir la base de connaissances** indiquera **Gestion de l'arborescence du domaine**. Après avoir cliqué sur **Fermer**, revenez à l'écran **Gestion de l'arborescence du domaine** pour effectuer l'activité de découverte des connaissances, cliquez sur **Terminer**, puis sur **Oui** pour publier la base de connaissances ou sur **Non** pour enregistrer le travail dans la base de connaissances et quitter.  Pour plus d'informations sur l'ouverture d'une base de connaissances verrouillée, consultez [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).  
  
  
