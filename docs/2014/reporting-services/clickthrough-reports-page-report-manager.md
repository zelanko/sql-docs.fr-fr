---
title: Page (Gestionnaire de rapports) rapports générés interactifs | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.modelproperties.drilthroughreports.f1
ms.assetid: e96cdeba-452b-45a8-9bcf-b75d76261e31
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d996463baaed3095b6866fa2da88ed811745878d
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66109794"
---
# <a name="clickthrough-reports-page-report-manager"></a>Page Rapports générés interactifs (Gestionnaire de rapports)
  Un rapport généré interactif affiche une table de données associées lorsque vous cliquez sur les données interactives contenues dans votre rapport. Ces rapports sont générés par le serveur de rapports à partir des informations contenues dans le modèle utilisé pour créer le rapport. Si vous ne souhaitez pas utiliser les rapports générés interactifs que le serveur de rapports génère, vous pouvez créer des rapports personnalisés que vous publiez sur un serveur de rapports et mappez aux points de données interactifs définis dans le modèle. Les rapports personnalisés doivent être créés dans le Générateur de rapports à partir du même modèle, puis publiés sur le serveur de rapports. Pour mapper des rapports personnalisés aux éléments dans le modèle, utilisez la page Rapports générés interactifs dans le Gestionnaire de rapports.  
  
 La page Rapports générés interactifs permet de mapper des rapports du Générateur de rapports prédéfinis et publiés aux entités, dossiers et éléments spécifiques dans un modèle. Lorsque vous mappez un rapport à un élément d'un modèle, les utilisateurs qui accèdent à cet élément obtiennent le rapport personnalisé plutôt qu'un rapport temporaire généré par le serveur de rapports.  
  
 Si vous fournissez des rapports personnalisés, vous devez inclure une version à instance unique et une version à plusieurs instances du rapport. Le chemin d'accès aux données par lequel un utilisateur atteint une entité spécifique détermine si un rapport à instance unique ou un rapport à plusieurs instances est présenté à l'utilisateur lors de l'exécution. Il n'est pas toujours possible de savoir à l'avance si une version particulière du rapport est superflue.  
  
 Les rapports personnalisés mappés aux entités sont sécurisés par le biais de l'arborescence des dossiers du serveur de rapports. Si vous mappez un élément de modèle à un rapport et que le rapport n'est pas disponible pour un utilisateur qui l'a atteint, l'utilisateur obtient un rapport temporaire généré par le serveur de rapports plutôt que le rapport personnalisé prévu.  
  
 Bien qu'il soit possible de sélectionner tous les rapports auxquels vous avez accès, sélectionnez uniquement les rapports créés spécifiquement pour le modèle que vous configurez.  
  
> [!NOTE]  
>  Les rapports générés interactifs ne sont pas disponibles dans toutes les éditions de [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour obtenir une liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], consultez [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md). Si vous ne savez pas précisément quelle est l'édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qu'utilise votre organisation, contactez votre administrateur de base de données.  
  
## <a name="navigation"></a>Navigation  
 Utilisez la procédure suivante pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
###### <a name="to-open-the-clickthrough-reports-page"></a>Pour ouvrir la page Rapports générés interactifs  
  
1.  Ouvrez le Gestionnaire de rapports et recherchez le modèle pour lequel vous souhaitez mapper des rapports générés interactifs aux entités dans le modèle.  
  
2.  Pointez sur le modèle et cliquez sur la flèche déroulante.  
  
3.  Dans le menu déroulant, cliquez sur **Gérer**. La page des propriétés **générales** pour le modèle s'ouvre.  
  
4.  Sélectionnez l'onglet **Rapports générés interactifs** .  
  
## <a name="options"></a>Options  
 **Hiérarchie de l’élément de modèle**  
 Affiche les entités, dossiers et éléments de l'espace de noms du modèle pour lesquels vous pouvez fournir un rapport personnalisé.  
  
 **Rapport d’instance unique**  
 Spécifie le rapport personnalisé à utiliser lorsque la navigation par l'utilisateur nécessite une vue des données à instance unique. Cliquez sur le bouton Parcourir pour sélectionner le rapport à utiliser.  
  
 **Rapport à plusieurs instances**  
 Spécifie le rapport personnalisé à utiliser lorsque la navigation par l'utilisateur nécessite une vue des données à plusieurs instances. Cliquez sur le bouton Parcourir pour sélectionner le rapport à utiliser.  
  
## <a name="see-also"></a>Voir aussi  
 [Publier des rapports](../../2014/reporting-services/publish-reports.md)  
  
  
