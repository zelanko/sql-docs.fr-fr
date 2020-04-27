---
title: Se connecter à une base de données Teradata (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connterradb.f1
ms.assetid: 875ad4a3-a2b3-4b68-8c1c-6507e9f25b4d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dc6712598452b1957857509e6b3ff6f659a16c4b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66087190"
---
# <a name="connect-to-a-teradata-database-ssas"></a>Connexion à une base de données Teradata (SSAS)
  Cette page de **l’Assistant Importation de table** vous permet de spécifier des paramètres pour vous connecter à une base de données Teradata. Pour accéder à l'Assistant [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], dans le menu **Modèle** , cliquez sur **Importer à partir de la source de données**.  
  
 Pour vous connecter à une source de données, vous devez disposer du fournisseur approprié, installé sur votre ordinateur.  
  
> [!NOTE]  
>  Les informations d'identification de l'utilisateur actuel sont utilisées lors de la sélection d'une base de données sur cette page. Toutefois, l'importation ne réussira pas si l'utilisateur spécifié dans la page Informations d'emprunt d'identité n'a pas de privilèges suffisants pour lire la base de données sélectionnée.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 **Nom convivial de la connexion**  
 Tapez un nom unique pour cette connexion à la source de données. Ce champ est obligatoire.  
  
 **Nom du serveur**  
 Tapez ou sélectionnez le nom de l'instance de serveur à laquelle se connecter.  
  
 **Nom d'utilisateur**  
 Spécifiez un nom d'utilisateur pour la connexion de base de données.  
  
 Ce nom d'utilisateur est utilisé lors de la construction de la chaîne de connexion pour la source de données. Ces informations d'identification sont également utilisées lors de l'affichage un aperçu et du filtrage des données dans la fenêtre Propriétés de la table et dans l'Assistant Importation. Ces informations d'identification ne sont pas utilisées pour importer ou actualiser des données ; les informations d'identification Windows spécifiées dans la page Informations d'emprunt d'identité sont utilisées à la place.  
  
 **Mot de passe**  
 Spécifiez un mot de passe pour la connexion de base de données.  
  
 **Enregistrer mon mot de passe**  
 Spécifiez si le mot de passe que vous avez entré dans la zone **Mot de passe** doit être mémorisé.  
  
 **Avancé**  
 Définissez des propriétés de connexion supplémentaires à l’aide de la boîte de dialogue **Définir les propriétés avancées** . Pour plus d’informations, consultez [Définir les propriétés avancées &#40;SSAS&#41;](set-advanced-properties-ssas.md).  
  
 **Tester la connexion**  
 Essayez d'établir une connexion à la source de données à l'aide des paramètres actuels. Un message est affiché pour indiquer si la connexion a abouti.  
  
  
