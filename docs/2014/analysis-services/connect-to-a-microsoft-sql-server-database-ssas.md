---
title: Se connecter à une base de données Microsoft SQL Server (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsqlserverdb.f1
ms.assetid: 6ebfe029-dbba-4f0d-a556-328e79ef629f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cc3530c7bc316c0dbdc3271d456d4f7adf05038a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66087215"
---
# <a name="connect-to-a-microsoft-sql-server-database-ssas"></a>Connexion à une base de données Microsoft SQL Server (SSAS)
  Cette page de **l’Assistant Importation de table** vous permet de spécifier des paramètres pour vous connecter à une base de données Microsoft SQL Server. Pour accéder à l'Assistant du [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], dans le menu **Modèle** , cliquez sur **Importer à partir de la source de données**.  
  
 Pour vous connecter à une source de données, vous devez disposer du fournisseur approprié, installé sur votre ordinateur.  
  
> [!NOTE]  
>  Les informations d'identification de l'utilisateur actuel sont utilisées lors de la sélection d'une base de données sur cette page. Toutefois, l'importation ne réussira pas si l'utilisateur spécifié dans la page Informations d'emprunt d'identité n'a pas de privilèges suffisants pour lire la base de données sélectionnée.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 **Nom convivial de connexion**  
 Tapez un nom unique pour cette connexion à la source de données. Ce champ est obligatoire.  
  
 **Nom du serveur**  
 Sélectionnez le nom ou tapez le nom ou l’adresse IP de l’instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à laquelle vous connecter.  
  
 Vous pouvez utiliser un point (.), (local) ou localhost pour indiquer le serveur local.  
  
 **Utiliser l'authentification Windows**  
 Précisez si l’authentification Windows est utilisée pour se connecter à une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Le mode d’authentification Windows permet à l’utilisateur de se connecter au moyen d’un compte d’utilisateur Windows. Dans la mesure du possible, utilisez l’authentification Windows.  
  
 Lorsque l'Authentification Windows est utilisée, les informations d'identification de l'utilisateur actuel sont utilisées lors de l'affichage d'un aperçu et le filtrage des données dans la fenêtre Propriétés de la table et dans l'Assistant Importation. Ces informations d'identification ne sont pas utilisées pour importer ou actualiser des données ; les informations d'identification Windows spécifiées dans la page Informations d'emprunt d'identité sont utilisées à la place.  
  
 **Utiliser l’authentification SQL Server**  
 Précisez si l’authentification SQL Server est utilisée pour se connecter à une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Avec l'authentification SQL Server, SQL Server effectue l'authentification lui-même en vérifiant si un compte de connexion SQL Server a été configuré et si le mot de passe spécifié correspond à celui enregistré précédemment.  
  
 L'Authentification SQL Server est utilisée pour construire la chaîne de connexion pour la source de données. Ces informations d'identification sont également utilisées lors de l'affichage un aperçu et du filtrage des données dans la fenêtre Propriétés de la table et dans l'Assistant Importation. Ces informations d'identification ne sont pas utilisées pour importer ou actualiser des données ; les informations d'identification Windows spécifiées dans la page Informations d'emprunt d'identité sont utilisées à la place.  
  
 **Nom d'utilisateur**  
 Spécifiez un nom d'utilisateur pour la connexion de base de données. Cette option est disponible uniquement si vous avez choisi de vous connecter via l'authentification SQL Server.  
  
 **Mot de passe**  
 Spécifiez un mot de passe pour la connexion de base de données. Cette option peut être modifiée uniquement si vous avez choisi de vous connecter via l'authentification SQL Server.  
  
 **Enregistrer mon mot de passe**  
 Précisez si le mot de passe que vous avez entré dans la zone **Mot de passe** est mémorisé. Cette option est disponible uniquement si vous avez choisi de vous connecter via l'authentification SQL Server.  
  
 **Nom de la base de données**  
 Sélectionnez une base de données dans la liste.  
  
 **Avancé**  
 Définissez des propriétés de connexion supplémentaires à l’aide de la boîte de dialogue **Définir les propriétés avancées** . Pour plus d’informations, consultez [Définir les propriétés avancées &#40;SSAS&#41;](set-advanced-properties-ssas.md).  
  
 **Tester la connexion**  
 Essayez d'établir une connexion à la source de données à l'aide des paramètres actuels. Un message s’affiche pour indiquer si la connexion a abouti.  
  
  
