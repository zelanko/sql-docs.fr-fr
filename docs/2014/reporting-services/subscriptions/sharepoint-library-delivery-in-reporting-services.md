---
title: Remise à une bibliothèque SharePoint dans Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SharePoint integration [Reporting Services], report delivery
- delivering reports [Reporting Services]
- subscriptions [Reporting Services], SharePoint library delivery
ms.assetid: cb4e4f71-f2d5-475a-9284-ea324c93c7de
caps.latest.revision: 15
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: e26aab503c41cbd64f16708c8b420bf3ae93af1f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142633"
---
# <a name="sharepoint-library-delivery-in-reporting-services"></a>Remise à une bibliothèque SharePoint dans Reporting Services
  Un serveur de rapports configuré en mode intégré SharePoint inclut une extension de remise que vous pouvez utiliser pour envoyer un rapport à une bibliothèque SharePoint.  
  
 Pour utiliser l’extension de remise SharePoint, vous devez créer un abonnement dans une page d’application sur un site SharePoint, puis sélectionner **Bibliothèque de documents SharePoint** comme type de remise. Vous ne pouvez pas utiliser l’extension de remise SharePoint pour des abonnements que vous créez dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ou le Gestionnaire de rapports.  
  
> [!NOTE]  
>  L'extension de remise ne prend pas en charge la remise des rapports à un site SharePoint si le serveur de rapports s'exécute en mode natif. Si vous tentez d'appeler par programme l'extension de remise pour un serveur de rapports en mode natif, le serveur retourne l'erreur `rsDeliveryExtensionNotFound` et enregistre l'erreur `rsOperationNotSupportedSharePointMode` dans les fichiers journaux du serveur de rapports.  
  
## <a name="requirements"></a>Spécifications  
 La configuration requise pour la remise des rapports rendus à une bibliothèque incluent ce qui suit :  
  
-   Le serveur de rapports doit être configuré pour le mode d'intégration SharePoint.  
  
-   Le serveur de rapports doit avoir l'extension de remise SharePoint installée et configurée.  
  
-   Le rapport doit être un fichier de définition de rapport (.rdl). Vous ne pouvez pas remettre d'autres types de contenu de serveur de rapports, tels que des modèles ou des ressources, via un abonnement. Vous ne pouvez pas vous abonner à des rapports ad hoc qui utilisent les modèles comme source de données.  
  
-   Le rapport doit utiliser des informations d'identification. Il s'agit d'une condition préalable à la création d'un abonnement sur un rapport, quel que soit le type de remise.  
  
-   La destination doit être une bibliothèque SharePoint. Lorsque vous choisissez une bibliothèque cible, vous devez en choisir une figurant sur le même site SharePoint. Vous ne pouvez pas remettre un rapport dans une bibliothèque sur un autre serveur ou un autre site au sein de la même collection de sites.  
  
 Les propriétés et les métadonnées n'appartiennent pas à la remise de rapports. Lorsque le rapport est remis pour la première fois, il hérite des paramètres de sécurité du dossier ou de la liste qui le contient. Si vous modifiez ensuite des paramètres de sécurité ou définissez des propriétés de rapport, ces paramètres sont retenus. L'abonnement actualise simplement le rapport stocké à l'emplacement spécifié.  
  
## <a name="sharepoint-permissions"></a>Autorisation SharePoint  
 Pour créer l'abonnement, vous devez disposer de l'autorisation Afficher des éléments sur le rapport. Pour remettre le rapport, vous devez avoir l'autorisation Ajouter des éléments dans la bibliothèque à laquelle le rapport est remis.  
  
## <a name="how-to-create-modify-and-delete-subscriptions"></a>Procédure de création, de modification ou de suppression des abonnements.  
  
1.  Accédez au site SharePoint à partir duquel vous accédez au rapport.  
  
2.  Sélectionnez le rapport, cliquez sur la flèche orientée vers le bas à côté du rapport, puis sélectionnez **Gérer les abonnements**.  
  
3.  Cliquez sur **Créer**, **Modifier**ou **Supprimer**.  
  
 Un message de statut sur la liste de gestion des abonnements affiche des informations actuelles sur l'abonnement, en particulier si celui-ci a abouti ainsi que l'heure et la date du dernier abonnement.  
  
## <a name="setting-delivery-options"></a>Définition des options de remise  
 Vous pouvez définir les options suivantes de remise sur un abonnement qui remet un rapport à une bibliothèque SharePoint.  
  
 Format de la sortie du rendu  
 Spécifiez le format de l'application dans lequel vous souhaitez remettre le rapport. Le rapport est rendu dans ce format avant la remise. Le format de sortie sélectionné détermine l'extension de fichier par défaut.  
  
 La liste des formats de sortie disponible est l'ensemble des extensions de rendu installées sur le serveur de rapports.  
  
 Remarquez que vous ne pouvez pas spécifier des formats de sortie réservés à un usage interne ou qui ne sont pas pris en charge par des serveurs de rapport qui s'exécutent en mode intégré SharePoint. Ces formats sont Null, RGDI et HTMLOWC.  
  
 Nom et extension de fichier  
 Spécifiez le nom et l'extension de fichier du rapport tel que vous souhaitez qu'ils apparaissent dans la bibliothèque cible. Si vous ne spécifiez d'extension de fichier, le serveur de rapports va en créer une basée sur le format de sortie du rapport. Cette valeur est requise. Le nom de fichier ne doit pas inclure les caractères suivants : : \ / * ? « \< > | # { } %  
  
 Titre  
 Spécifie éventuellement une `Title` propriété pour le rapport dans la bibliothèque cible. Il s'agit d'une propriété standard pour tous les éléments stockés dans une bibliothèque. Les utilisateurs peuvent choisir de montrer ou de masquer cette propriété lorsqu'ils consultent le contenu de la bibliothèque sur un site SharePoint.  
  
 Chemin d'accès  
 Spécifie une URL complète vers la bibliothèque SharePoint, notamment l'application et le site Web SharePoint. Par exemple : http://mySharePointWeb/MySite/MyDocLib, où «http://mySharePointWeb» indique l’application Web, « MySite » est le site SharePoint, et « MyDocLib » est la bibliothèque SharePoint où le rapport est remis.  
  
 Vous ne pouvez pas spécifier une page, un site ou une liste. Le conteneur cible doit être une bibliothèque dans le même site ou batterie de serveurs.  
  
 Options de remplacement  
 Spécifie si un fichier du même nom et extension est remplacé par une version plus récente lorsque l'abonnement est traité. Sélectionnez **Remplacer** si vous souhaitez remplacer un fichier existant par une nouvelle version. Sélectionnez **Aucune** si vous ne souhaitez pas que l’abonnement remplace un fichier. Dans ce cas, aucune remise ne se produit s'il existe un fichier avec les mêmes nom et extension. Sélectionnez **Auto-incrément** si vous souhaitez ajouter des versions successives du même fichier en ajoutant un numéro à la fin du nom du fichier.  
  
 Copie automatique  
 Si vous utilisez cette fonctionnalité pour copier automatiquement la dernière version d’un fichier dans plusieurs emplacements, le fichier est copié si l’option **Remplacer** est activée. Si vous avez utilisé **Autoincrement** ou **aucun**, la remise échoue et le `rsDeliveryError` erreur se produit.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer et gérer des abonnements pour les serveurs de rapports en Mode SharePoint](create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md)   
 [Abonnements et remises &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md)   
 [Spécifier des informations d'identification et de connexion pour les sources de données de rapports](../report-data/specify-credential-and-connection-information-for-report-data-sources.md)  
  
  