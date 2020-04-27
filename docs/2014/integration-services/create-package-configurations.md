---
title: Créer des configurations de package | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Integration Services packages, configurations
- Package Configurations Organizer dialog box
- SSIS packages, configurations
- Integration Services packages, configurations
- configurations [Integration Services]
- packages [Integration Services], configurations
- deploying packages [Integration Services], configurations
ms.assetid: 91ac0347-f908-44f5-bd3d-115790223af4
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 287ac1a5631cf2e3925e5895db7f04bb7b89bf5d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66060167"
---
# <a name="create-package-configurations"></a>Créer des configurations de package
  Vous pouvez créer des configurations de package à l'aide de la boîte de dialogue **Bibliothèque des configurations du package** et de l'Assistant Configuration de package. Pour accéder à ces outils, cliquez sur **Configurations du package** dans le menu **SSIS** de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
> [!NOTE]  
>  Vous pouvez également accéder à l' **organiseur de configuration de package**en cliquant sur le bouton de sélection en regard de la propriété de **configuration** . La propriété Configuration apparaît dans la fenêtre des propriétés du package.  
  
> [!NOTE]  
>  Des configurations sont disponibles pour le modèle de déploiement de package. Les paramètres sont utilisés à la place des configurations pour le modèle de déploiement de projet. Le modèle de déploiement de projet vous permet de déployer des projets [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur le serveur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Pour plus d'informations sur les modèles de déploiement, consultez [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).  
  
 Dans la boîte de dialogue **Bibliothèque des configurations du package** , vous pouvez permettre aux packages d'utiliser des configurations, ajouter et supprimer des configurations et définir l'ordre souhaité dans lequel sont chargées les configurations.  
  
> [!NOTE]  
>  Lorsque les configurations du package sont chargées dans l'ordre souhaité, le chargement est effectué du haut vers le bas de la liste affichée dans la boîte de dialogue **Bibliothèques des configurations du package** . Toutefois, au moment de l'exécution, il se peut que les configurations de package ne soient pas chargées dans l'ordre souhaité. Les configurations de package parent sont notamment chargées après les configurations d'autres types.  
  
> [!NOTE]  
>  Si plusieurs configurations définissent la même propriété d'objet, la dernière valeur chargée est utilisée à l'exécution.  
  
 À partir de la boîte de dialogue **Bibliothèque des configurations du package** , vous pouvez exécuter l'Assistant Configuration de package, qui vous guide à travers les étapes de création d'une configuration. Pour exécuter l'Assistant Configuration de package, ajoutez une nouvelle configuration dans la boîte de dialogue **Bibliothèque des configurations du package** ou modifiez une configuration existante. Sur les pages de l'Assistant, vous choisissez un type de configuration, vous choisissez si vous souhaitez accéder directement à la configuration ou utiliser des variables d'environnement, et vous sélectionnez les propriétés à enregistrer dans la configuration.  
  
 L'exemple suivant illustre les propriétés cibles d'une variable et d'un package telles qu'elles apparaissent dans la page Fin de l'Assistant de l'Assistant Configuration de package :  
  
 \Package.Variables[User::TodaysDate].Properties[RaiseChangedEvent]  
  
 \Package.Properties[MaximumErrorCount]  
  
 \Package.Properties[LoggingMode]  
  
 \Package.Properties[LocaleID]  
  
 \Package\My SQL Task.Variables[User::varTableName].Properties[Value]  
  
 Dans cet exemple, la configuration met à jour ces propriétés :  
  
-   Propriété RaiseChangedEvent de la variable définie par l’utilisateur `TodaysDate`  
  
-   Propriétés MaximumErrorCount, LoggingMode et LocaleID du package  
  
-   Propriété Value de la variable définie par l’utilisateur `varTableName`, dans la portée de la tâche My SQL Task  
  
 La syntaxe « \Package » représente la racine, et les points (.) séparent les objets qui définissent le chemin d'accès de la propriété mise à jour par la configuration. Les noms de variables et de propriétés figurent entre crochets. Le terme Package est toujours utilisé dans la configuration, quel que soit le nom du package ; toutefois, tous les autres objets indiqués dans le chemin d'accès portent leur nom défini par l'utilisateur.  
  
 Une fois l'Assistant terminé, la nouvelle configuration est ajoutée à la liste des configurations dans la boîte de dialogue **Bibliothèque des configurations du package** .  
  
> [!NOTE]  
>  La dernière page de l'Assistant Configuration de package, Fin de l'Assistant, répertorie les propriétés cibles dans la configuration. Si vous souhaitez mettre à jour des propriétés pendant l’exécution de packages à l’aide de l’utilitaire d’invite de commandes **dtexec** , vous pouvez générer les chaînes qui représentent les chemins d’accès aux propriétés en exécutant l’Assistant Configuration de package, puis les copier et les coller dans la fenêtre d’invite de commandes pour les utiliser avec l’option set de **dtexec**.  
  
 Le tableau suivant décrit les colonnes dans la liste des configurations de la boîte de dialogue **Bibliothèque des configurations du package** .  
  
|Colonne|Description|  
|------------|-----------------|  
|**Nom de la configuration**|Le nom de la configuration.|  
|**Type de configuration**|Le type de la configuration.|  
|**Chaîne de configuration**|L'emplacement de la configuration. L'emplacement peut être un chemin d'accès, une variable d'environnement, une clé de Registre, un nom de variable d'un package parent ou une table d'une base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|  
|**Objet cible**|Le nom de l'objet dont une propriété a une configuration. Si la configuration est un fichier de configuration XML, la colonne est vide, car la configuration peut mettre à jour plusieurs objets.|  
|**Propriété cible**|Nom de la propriété. Si la configuration écrit dans un fichier de configuration XML ou dans une table SQL Server, la colonne est vide puisque la configuration peut mettre à jour plusieurs objets.|  
  
### <a name="to-create-a-package-configuration"></a>Pour créer une configuration de package  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] , cliquez sur l'onglet **Flux de contrôle**, **Flux de données**, **Gestionnaire d'événements**ou **Explorateur de package** .  
  
4.  Dans le menu **SSIS** , cliquez sur **Configurations du package**.  
  
5.  Dans la boîte de dialogue **Bibliothèque des configurations du package** , sélectionnez **Activer les configurations du package**et cliquez sur **Ajouter**.  
  
6.  Sur la page d'accueil de l'Assistant Configuration de package, cliquez sur **Suivant**.  
  
7.  Sur la page Sélectionner le type de configuration, spécifiez le type de configuration, puis définissez les propriétés se rapportant au type de configuration. Pour plus d’informations, voir [Package Configuration Wizard UI Reference](../../2014/integration-services/package-configuration-wizard-ui-reference.md).  
  
8.  Dans la page Sélectionner les propriétés à exporter, sélectionnez les propriétés des objets de package à inclure dans la configuration. Si le type de configuration ne prend en charge qu'une seule propriété, le titre de cette page de l'Assistant est Sélectionner la propriété cible. Pour plus d’informations, voir [Package Configuration Wizard UI Reference](../../2014/integration-services/package-configuration-wizard-ui-reference.md).  
  
    > [!NOTE]  
    >  Seuls les types de configuration **Fichier de configuration XML** et **SQL Server** prennent en charge l’inclusion de plusieurs propriétés dans une configuration.  
  
9. Dans la page Fin de l'Assistant, tapez le nom de la configuration, puis cliquez sur **Terminer**.  
  
10. Affichez la configuration dans la boîte de dialogue **Bibliothèque des configurations du package** .  
  
11. Cliquez sur **Fermer**.  
  
## <a name="external-resources"></a>Ressources externes  
  
-   Article technique, [Understanding Integration Services Package Configurations](https://go.microsoft.com/fwlink/?LinkId=165643), sur msdn.microsoft.com  
  
-   Entrée de blog, [création de packages dans le code-configurations de package](https://go.microsoft.com/fwlink/?LinkId=217663), sur www.SQLIS.com.  
  
-   Entrée de blog, [exemple d’API-ajouter par programmation un fichier de configuration à un package](https://go.microsoft.com/fwlink/?LinkId=217664), sur blogs.msdn.com.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurations du package](../../2014/integration-services/package-configurations.md)   
 [Déploiement de packages &#40;&#41;SSIS](packages/legacy-package-deployment-ssis.md)   
 [Utilisation de variables par programmation](building-packages-programmatically/working-with-variables-programmatically.md)  
  
  
