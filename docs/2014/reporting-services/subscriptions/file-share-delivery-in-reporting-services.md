---
title: Remise par partage de fichiers dans Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], file share delivery
- file share delivery [Reporting Services]
ms.assetid: 9f338dd3-f68a-4355-b9d7-9b25dacf3b5e
caps.latest.revision: 52
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e4123ae77852bf0ccde4229644393f8160ffb391
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37331209"
---
# <a name="file-share-delivery-in-reporting-services"></a>Remise par partage de fichiers dans Reporting Services
  SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] comprend une extension de remise de partage de fichiers qui vous permet de remettre un rapport dans un dossier. Cette extension est disponible par défaut et elle ne nécessite aucune configuration supplémentaire. Pour que la remise de fichier réussisse, vous devez définir des autorisations d'accès en écriture sur le dossier partagé. En outre, les utilisateurs qui demandent l'accès aux rapports doivent avoir des autorisations de lecture sur le dossier partagé.  
  
 Pour distribuer un rapport dans un partage de fichiers, vous devez définir un abonnement standard ou piloté par les données. Vous ne pouvez vous abonner et ne demander la remise que d'un seul rapport à la fois. Pour savoir comment utiliser la remise par partage de fichiers pour un abonnement piloté par les données, consultez [Créer un abonnement piloté par les données &#40;didacticiel SSRS&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md). Par ailleurs, le compte qui exécute des abonnements de partage de fichiers distants nécessite des droits pour ouvrir une session locale sur l'ordinateur [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint|  
  
 Dans cette rubrique :  
  
-   [Caractéristiques d’un rapport est remis dans un dossier partagé](#bkmk_Characteristics)  
  
-   [Dossiers cibles](#bkmk_target_folders)  
  
-   [Formats de fichier](#bkmk_file_formats)  
  
-   [Options de fichier](#bkmk_file_options)  
  
##  <a name="bkmk_Characteristics"></a> Caractéristiques d’un rapport est remis dans un dossier partagé  
 Contrairement aux rapports qui sont hébergés et gérés par un serveur de rapports, les rapports qui sont remis dans un dossier partagé sont des fichiers statiques. Les fonctionnalités interactives qui sont définies pour le rapport ne fonctionnent pas pour les rapports qui sont stockés en tant que fichiers dans le système de fichiers. Les fonctionnalités d'interaction sont représentées comme des éléments statiques. Par exemple, si vous remettez un rapport de matrice, le fichier généré offre une vue de niveau supérieur du rapport ; vous ne pouvez pas étendre les lignes et les colonnes pour afficher les données associées. Si le rapport contient des graphiques, la présentation par défaut est utilisée. Si le rapport contient un lien vers un autre rapport, le lien apparaît sous forme de texte statique. Si vous voulez conserver les fonctionnalités interactives dans un rapport remis, utilisez la remise par courrier électronique à la place. Pour plus d’informations, consultez [Remise par courrier électronique dans Reporting Services](e-mail-delivery-in-reporting-services.md).  
  
##  <a name="bkmk_target_folders"></a> Dossiers cibles  
 Lorsque vous définissez un abonnement qui utilise la remise dans un partage de fichiers, vous devez spécifier un dossier existant comme dossier cible. Le serveur de rapports ne crée pas de dossiers sur le système de fichiers. Le dossier que vous spécifiez doit être accessible via une connexion réseau.  
  
 Vérifiez que les utilisateurs qui afficheront les rapports dans le dossier partagé ont une autorisation Lecture.  
  
 Lors de la spécification d'un dossier cible dans un abonnement, utilisez le format UNC (Uniform Naming Convention) qui inclut le nom réseau de l'ordinateur. N'incluez pas de barre oblique inverse à la fin du chemin d'accès au dossier. L'exemple suivant illustre un chemin UNC :  
  
```  
\\<servername>\reportarchive\operations\2003  
```  
  
 Lorsque vous créez le dossier, tenez compte des limites de connexion requises. Le serveur de rapports nécessite deux connexions, mais vous devez inclure suffisamment de connexions pour la prise en charge des utilisateurs complémentaires qui veulent ouvrir des rapports sur le dossier partagé.  
  
##  <a name="bkmk_file_formats"></a> Formats de fichier  
 Les rapports peuvent être rendus dans plusieurs formats de fichier, tels que HTML ou Excel. Pour enregistrer le rapport dans un format de fichier spécifique, sélectionnez le format de rendu au moment de la création de l'abonnement. Par exemple, en choisissant **Excel** , vous enregistrez le rapport sous la forme d'un fichier [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] . Bien que vous puissiez choisir n'importe quel format de rendu pris en charge, certains formats sont mieux adaptés que d'autres.  
  
 Pour la remise par partage de fichiers, choisissez un format qui assure la remise du rapport dans un seul fichier, où toutes les images et le contenu associé sont inclus dans le rapport. Les formats appropriés sont les suivants : archive Web, PDF, TIFF et Excel. Évitez le format HTML 4.0. Si votre rapport comporte des images, le format HTML 4.0 ne permettra pas de les inclure dans le fichier.  
  
##  <a name="bkmk_file_options"></a> Options de fichier  
 Lorsque vous créez un abonnement, vous pouvez choisir les options qui déterminent comment le nom de fichier est créé et s'il est remplacé par des versions plus récentes dans le temps. Un nom de fichier complet comprend trois parties : un nom, une extension et du texte ou un nombre ajouté au fichier pour créer un nom de fichier unique. Les options de remplacement déterminent si le texte ou le nombre est ajouté au nom de fichier.  
  
 Le nom de fichier est basé sur le nom du rapport, mais vous pouvez indiquer un nom personnalisé dans l'abonnement. L'extension est facultative, mais si vous la spécifiez, le serveur de rapports créera une extension qui correspond au format de rendu.  
  
 Vous pouvez spécifier des options de remplacement afin de réutiliser le même nom de fichier pour chaque remise de rapport ou pour créer un nouveau fichier. Pour remplacer le fichier, vous devez utiliser les mêmes nom et extension de fichier.  
  
 Pour créer des noms de fichiers uniques pour la remise de rapport, il existe une autre approche qui consiste à inclure un élément d'horodatage dans le nom de fichier. Pour ce faire, ajoutez le `@timestamp` variable pour le nom de fichier (par exemple, *CompanySales@timestamp*). Avec cette approche, le nom de fichier est unique par définition : il ne sera jamais remplacé.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer, modifier et supprimer des abonnements Standard &#40;Reporting Services en Mode natif&#41;](create-and-manage-subscriptions-for-native-mode-report-servers.md)  
  
  
