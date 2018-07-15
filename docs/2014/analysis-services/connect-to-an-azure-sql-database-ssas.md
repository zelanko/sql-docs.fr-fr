---
title: Se connecter à une base de données SQL Azure (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsqlazure.f1
ms.assetid: 4e0344e9-1822-4698-ad22-05f1f341ced7
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1caee43f182c92c3a01193a852a067e20c9a579c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37214279"
---
# <a name="connect-to-an-azure-sql-database-ssas"></a>Connexion à une base de données Azure SQL Database (SSAS)
  Cette page de **l’Assistant Importation de table** vous permet de vous connecter à une [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)]. Pour accéder à l'Assistant [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], dans le menu **Modèle** , cliquez sur **Importer à partir de la source de données**.  
  
> [!NOTE]  
>  Si vous vous connectez à un dataset Azure DataMarket, consultez [Connexion à un flux de rapport ou de données &#40;SSAS&#41;](connect-to-a-report-or-data-feed-ssas.md).  
  
 La [!INCLUDE[ssSDS](../includes/sssds-md.md)] est une base de données relationnelle hébergée à laquelle vous vous connectez à l'aide de l'authentification SQL Server. Pour plus d'informations sur [!INCLUDE[ssSDS](../includes/sssds-md.md)], consultez le site Web [Base de données SQL](http://go.microsoft.com/fwlink/?LinkID=157856). Pour vous connecter à une source de données, vous devez disposer du fournisseur approprié, installé sur votre ordinateur.  
  
> [!NOTE]  
>  Les informations d'identification de l'utilisateur actuel sont utilisées lors de la sélection d'une base de données sur cette page. Toutefois, l'importation ne réussira pas si l'utilisateur spécifié dans la page Informations d'emprunt d'identité n'a pas de privilèges suffisants pour lire la base de données sélectionnée.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 **Nom convivial de connexion**  
 Tapez un nom unique pour cette connexion à la source de données. Ce champ est obligatoire.  
  
 **Nom du serveur**  
 Tapez le nom ou l'adresse IP du serveur auquel se connecter.  
  
 **Nom d'utilisateur**  
 Spécifiez un nom d'utilisateur pour la connexion de base de données.  
  
 Ce nom d'utilisateur est utilisé lors de la construction de la chaîne de connexion pour la source de données. Ces informations d'identification sont également utilisées lors de l'affichage un aperçu et du filtrage des données dans la fenêtre Propriétés de la table et dans l'Assistant Importation. Ces informations d'identification ne sont pas utilisées pour importer ou actualiser des données ; les informations d'identification Windows spécifiées dans la page Informations d'emprunt d'identité sont utilisées à la place.  
  
 **Mot de passe**  
 Spécifiez un mot de passe pour la connexion de base de données.  
  
 **Enregistrer mon mot de passe**  
 Précisez si le mot de passe que vous avez entré dans la zone **Mot de passe** est mémorisé.  
  
 **Nom de la base de données**  
 Sélectionnez une base de données dans la liste.  
  
 **Avancé**  
 Définissez des propriétés de connexion supplémentaires à l’aide de la boîte de dialogue **Définir les propriétés avancées** . Pour plus d’informations, consultez [Définir les propriétés avancées &#40;SSAS&#41;](set-advanced-properties-ssas.md).  
  
 **Tester la connexion**  
 Essayez d'établir une connexion à la source de données à l'aide des paramètres actuels. Un message est affiché pour indiquer si la connexion a abouti.  
  
  
