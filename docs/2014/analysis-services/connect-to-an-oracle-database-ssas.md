---
title: Se connecter à une base de données Oracle (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connoracledb.f1
ms.assetid: 9bd177fb-8539-46cd-bf96-189ade52c2a1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 79808c965828844a467fc232a5432d1207b25c34
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48058501"
---
# <a name="connect-to-an-oracle-database-ssas"></a>Connexion à une base de données Oracle (SSAS)
  Cette page de l' **Assistant Importation de table** vous permet de spécifier des paramètres pour vous connecter à une base de données Oracle. Pour accéder à l'Assistant [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], dans le menu **Modèle** , cliquez sur **Importer à partir de la source de données**.  
  
 Pour vous connecter à une source de données, vous devez disposer du fournisseur approprié, installé sur votre ordinateur.  
  
> [!NOTE]  
>  Les informations d'identification de l'utilisateur actuel sont utilisées lors de la sélection d'une base de données sur cette page. Toutefois, l'importation ne réussira pas si l'utilisateur spécifié dans la page Informations d'emprunt d'identité n'a pas de privilèges suffisants pour lire la base de données sélectionnée.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 **Nom convivial de connexion**  
 Tapez un nom unique pour cette connexion à la source de données. Ce champ est obligatoire.  
  
 **Nom du serveur**  
 Tapez ou sélectionnez le nom de l'instance de serveur à laquelle se connecter.  
  
 **Nom d'utilisateur**  
 Spécifiez un nom d'utilisateur pour la connexion de base de données.  
  
 Ce nom d'utilisateur est utilisé lors de la construction de la chaîne de connexion pour la source de données. Ces informations d'identification sont également utilisées lors de l'affichage un aperçu et du filtrage des données dans la fenêtre Propriétés de la table et dans l'Assistant Importation. Ces informations d'identification ne sont pas utilisées pour importer ou actualiser des données ; les informations d'identification Windows spécifiées dans la page Informations d'emprunt d'identité sont utilisées à la place.  
  
 **Mot de passe**  
 Spécifiez un mot de passe pour la connexion de base de données.  
  
 **Enregistrer mon mot de passe**  
 Précisez si le mot de passe que vous avez entré dans la zone **Mot de passe** est mémorisé.  
  
 **Avancé**  
 Définissez des propriétés de connexion supplémentaires à l’aide de la boîte de dialogue **Définir les propriétés avancées** . Pour plus d’informations, consultez [Définir les propriétés avancées &#40;SSAS&#41;](set-advanced-properties-ssas.md).  
  
 **Tester la connexion**  
 Essayez d'établir une connexion à la source de données à l'aide des paramètres actuels. Un message est affiché pour indiquer si la connexion a abouti.  
  
  
