---
title: Se connecter à une base de données DB2 (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.conndb2db.f1
ms.assetid: eeef3697-a4fd-4263-ba7e-f86afa1f46cc
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 50818393a81cf3c6db1b54a0752e6fa098277709
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66087382"
---
# <a name="connect-to-a-db2-database-ssas"></a>Connexion à une base de données DB2 (SSAS)
  Cette page de l' **Assistant Importation de table** vous permet de spécifier des paramètres pour vous connecter à une base de données DB2. Pour accéder à l'Assistant [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], dans le menu **Modèle** , cliquez sur **Importer à partir de la source de données**.  
  
 Pour vous connecter à une source de données, vous devez disposer du fournisseur approprié, installé sur votre ordinateur.  
  
> [!NOTE]  
>  Lors de la sélection d'une base de données dans cette page, les informations d'identification de l'utilisateur spécifiées sont utilisées. Toutefois, l'importation ne réussira pas si l'utilisateur spécifié dans la page Informations d'emprunt d'identité n'a pas de privilèges suffisants pour lire la base de données sélectionnée.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 **Nom convivial de la connexion**  
 Tapez un nom unique pour cette connexion à la source de données. Ce champ est obligatoire.  
  
 **Nom du serveur**  
 Tapez ou sélectionnez l'instance de serveur à laquelle se connecter.  
  
 **Nom d'utilisateur**  
 Spécifiez un nom d'utilisateur pour la connexion de base de données.  
  
 Ce nom d'utilisateur est utilisé lors de la construction de la chaîne de connexion pour la source de données. Ces informations d'identification sont également utilisées lors de l'affichage un aperçu et du filtrage des données dans la fenêtre Propriétés de la table et dans l'Assistant Importation. Ces informations d'identification ne sont pas utilisées pour importer ou actualiser des données ; les informations d'identification Windows spécifiées dans la page Informations d'emprunt d'identité sont utilisées à la place.  
  
 **Mot de passe**  
 Spécifiez un mot de passe pour la connexion de base de données.  
  
 **Enregistrer mon mot de passe**  
 Spécifiez si le mot de passe que vous avez entré dans la zone **Mot de passe** est stocké.  
  
 **Nom de la base de données**  
 Sélectionnez une base de données dans la liste.  
  
 **Collection de packages**  
 Spécifiez le nom de la collection pour les packages DB2. Un fournisseur utilise des packages pour émettre des instructions SQL et appeler des procédures stockées.  
  
 **Schéma par défaut**  
 Spécifiez le nom du schéma par défaut de la base de données sélectionnée.  
  
 **Avancée**  
 Définissez des propriétés de connexion supplémentaires à l’aide de la boîte de dialogue **définir les propriétés avancées** .  
  
 **Tester la connexion**  
 Essayez d'établir une connexion à la source de données à l'aide des paramètres actuels. Un message est affiché pour indiquer si la connexion a abouti.  
  
  
