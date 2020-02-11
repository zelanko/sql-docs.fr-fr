---
title: Renommer une instance de Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- instances of Analysis Services, renaming
- renaming instances of Analysis Services
- names [Analysis Services], renaming instances
- names [Analysis Services]
ms.assetid: 87494741-4a2e-4fed-8061-418fd1e111c3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3ef94fc86c78e896eab03bffb318b58e4b328245
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66079621"
---
# <a name="rename-an-analysis-services-instance"></a>Renommer une instance d'Analysis Services
  Vous pouvez renommer une instance existante de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à l’aide de la boîte de dialogue **Renommer l’instance** .  
  
> [!IMPORTANT]  
>  Pendant que l’instance est renommée, l’utilitaire Modification du nom d’instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] s’exécute avec des privilèges élevés et met à jour le nom de service Windows, les comptes de sécurité et les entrées de Registre associées à cette instance. Pour vous assurer que ces actions sont effectuées, veillez à exécuter cet outil en tant qu'administrateur système local.  
  
 L’utilitaire Modification du nom d’instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne modifie pas le dossier du programme créé pour l’instance d’origine. Ne modifiez pas le nom du dossier du programme pour qu'il corresponde à l'instance que vous renommez. Le fait de modifier un nom de dossier de programme peut empêcher au programme d'installation de réparer ou désinstaller celle-ci.  
  
> [!NOTE]  
>  L’utilitaire Modification du nom d’instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] n’est pas pris en charge pour une utilisation dans un environnement de cluster.  
  
### <a name="to-rename-an-instance-of-analysis-services"></a>Pour renommer une instance d'Analysis Services  
  
1.  Lancez l’outil **modification du nom d’instance** , **asinstancerename. exe**, à partir de C:\Program Files\Microsoft SQL Server\110\Tools\Binn\ManagementStudio.  
  
2.  Dans la boîte de dialogue **Renommer l’instance** , sélectionnez dans la liste **Instance à renommer** l’instance que vous souhaitez renommer.  
  
3.  Dans la zone **Nouveau nom d’instance** , entrez le nouveau nom de l’instance.  
  
4.  Vérifiez que le nom d’utilisateur et le mot de passe sont corrects, puis cliquez sur **Renommer**.  
  
     L'instance Analysis Services sera arrêtée et redémarrée dans le cadre du changement de nom.  
  
### <a name="post-rename-checklist"></a>Liste de contrôle après la modification du nom  
  
1.  Pour récupérer l'accès aux bases de données qui s'exécutent sur l'instance renommée, vous devez mettre à jour manuellement les connexions de données dans Excel ou les autres applications clientes. Vérifiez également toutes les connexions prédéfinies, telles que les sources de données partagées Reporting Services, les fichiers ODC Excel ou les fichiers de connexion de modèle sémantique BI qui peuvent référencer l'instance que vous venez de renommer. Pour plus d’informations, consultez [Se connecter à Analysis Services](connect-to-analysis-services.md).  
  
2.  Mettez à jour les scripts PowerShell ou AMO (Analysis Management Objects) que vous utilisez régulièrement pour la sauvegarde, la synchronisation ou le traitement des bases de données.  
  
3.  Mettez à jour les propriétés des projets [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans lesquels vous travaillez dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Pour les instances de serveur en mode tabulaire, veillez à mettre à jour la propriété Serveur d'espace de travail dans le fichier model.bim, ainsi que la propriété Serveur dans le projet.  
  
4.  Selon la façon dont vous avez spécifié le compte de service, vous devrez peut-être mettre à jour les connexions à la base de données ou les autorisations de fichiers qui accordent des droits d'accès au service (par exemple, si vous utilisez le compte de service pour le traitement des données ou pour accéder aux objets liés sur un autre serveur).  
  
     La mise à jour d'une connexion à une base de données ou des autorisations de fichiers est nécessaire si vous avez utilisé un compte virtuel pour configurer le service. Les comptes virtuels sont basés sur le nom de l'instance, donc si vous renommez l'instance, le compte virtuel est également mis à jour. Cela signifie que toutes les connexions ou autorisations précédentes créées pour l'instance antérieure ne sont plus valides.  
  
     L'exemple suivant en est l'illustration. Supposons que vous avez installé un serveur en mode tabulaire en tant qu’instance nommée « Tabular » à l’aide du compte virtuel par défaut, ce qui entraîne la configuration suivante :  
  
    1.  Nom de l' \<instance = serveur> \tabular  
  
    2.  Nom du service = MSOLAP$TABULAR  
  
    3.  Compte virtuel = NT Service\ MSOLAP$TABULAR  
  
     Supposons à présent que vous renommez l’instance en « TAB2 ». Suite au changement de nom, la configuration se présente à présent comme suit :  
  
    1.  Nom de l' \<instance = serveur> \tab2  
  
    2.  Nom du service = MSOLAP$TAB2  
  
    3.  Compte virtuel = NT Service\ MSOLAP$TAB2  
  
     Comme vous pouvez le voir, les autorisations de base de données et de fichier précédemment accordées à « NT Service \ MSOLAP $ TABULAr » ne sont plus valides. Pour vous assurer que les tâches et les opérations effectuées par le service s’exécutent comme avant, vous devez maintenant accorder aux nouvelles autorisations de base de données et de fichier la valeur « NT Service \ MSOLAP $ TAB2 ».  
  
  
