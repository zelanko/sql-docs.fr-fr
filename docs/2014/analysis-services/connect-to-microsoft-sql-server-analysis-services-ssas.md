---
title: Se connecter à Microsoft SQL Server Analysis Services (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsqlserveras.f1
ms.assetid: 7f3244ee-b690-471c-893d-68e361c2d416
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 350251b6813027455f8e1e9b83dcf2508371df70
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48129849"
---
# <a name="connect-to-microsoft-sql-server-analysis-services-ssas"></a>Connexion à Microsoft SQL Server Analysis Services (SSAS)
  Cette page de l' **Assistant Importation de table** vous permet de spécifier les paramètres d'importation de données à partir d'un cube Microsoft SQL Server Analysis Services ou d'un classeur PowerPivot hébergé sur SharePoint. Pour accéder à l'Assistant [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], dans le menu **Modèle** , cliquez sur **Importer à partir de la source de données**.  
  
 Pour vous connecter à une source de données, vous devez disposer du fournisseur approprié, installé sur votre ordinateur.  
  
> [!NOTE]  
>  Les informations d'identification de l'utilisateur actuel sont utilisées lors de la sélection d'une base de données sur cette page. Toutefois, l'importation ne réussira pas si l'utilisateur spécifié dans la page Informations d'emprunt d'identité n'a pas de privilèges suffisants pour lire la base de données sélectionnée.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 **Nom convivial de connexion**  
 Tapez un nom unique pour cette connexion à la source de données. Ce champ est obligatoire.  
  
 **Nom de fichier ou de serveur**  
 Entrez l'une des informations suivantes :  
  
-   Tapez le nom ou l'adresse IP du serveur SQL Server Analysis Services auquel vous voulez vous connecter.  
  
     Vous pouvez utiliser un point (.), (local) ou localhost pour indiquer le serveur local.  
  
-   Tapez l'URL d'un classeur PowerPivot publié dans SharePoint.  
  
 **Utiliser l'authentification Windows**  
 Spécifiez si l'authentification Windows est utilisée pour se connecter à un serveur SQL Server Analysis Services.  
  
 Le mode d'authentification Windows permet à l'utilisateur de se connecter au moyen d'un compte d'utilisateur Windows. Dans la mesure du possible, utilisez l’authentification Windows.  
  
 Lorsque l'Authentification Windows est utilisée, les informations d'identification de l'utilisateur actuel sont utilisées lors de l'affichage d'un aperçu et le filtrage des données dans la fenêtre Propriétés de la table et dans l'Assistant Importation. Ces informations d'identification ne sont pas utilisées pour importer ou actualiser des données ; les informations d'identification Windows spécifiées dans la page Informations d'emprunt d'identité sont utilisées à la place.  
  
 **Utiliser l’authentification SQL Server**  
 Spécifiez si l'authentification SQL Server est utilisée pour se connecter à un serveur SQL Server Analysis Services.  
  
 Avec l'authentification SQL Server, SQL Server effectue l'authentification lui-même en vérifiant si un compte de connexion SQL Server a été configuré et si le mot de passe spécifié correspond à celui enregistré précédemment.  
  
 L'Authentification SQL Server est utilisée pour construire la chaîne de connexion pour la source de données. Ces informations d'identification sont également utilisées lors de l'affichage un aperçu et du filtrage des données dans la fenêtre Propriétés de la table et dans l'Assistant Importation. Ces informations d'identification ne sont pas utilisées pour importer ou actualiser des données ; les informations d'identification Windows spécifiées dans la page Informations d'emprunt d'identité sont utilisées à la place.  
  
 **Nom d'utilisateur**  
 Spécifiez un nom d'utilisateur pour la connexion de base de données. Cette option est uniquement disponible si vous avez choisi la connexion avec l'authentification Windows.  
  
 **Mot de passe**  
 Spécifiez un mot de passe pour la connexion de base de données. Cette option peut être modifiée uniquement si vous avez choisi de vous connecter via l'authentification SQL Server.  
  
 **Enregistrer mon mot de passe**  
 Précisez si le mot de passe que vous avez entré dans la zone **Mot de passe** est mémorisé. Cette option est disponible uniquement si vous avez choisi de vous connecter via l'authentification SQL Server.  
  
 **Nom de la base de données**  
 Sélectionnez une base de données dans la liste.  
  
 **Avancé**  
 Définissez des propriétés de connexion supplémentaires à l’aide de la boîte de dialogue **Définir les propriétés avancées** . Pour plus d’informations, consultez [Définir les propriétés avancées &#40;SSAS&#41;](set-advanced-properties-ssas.md).  
  
 **Tester la connexion**  
 Essayez d'établir une connexion à la source de données à l'aide des paramètres actuels. Un message est affiché pour indiquer si la connexion a abouti.  
  
  
