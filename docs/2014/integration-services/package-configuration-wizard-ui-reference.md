---
title: Informations de référence sur l’interface utilisateur de l’Assistant Configuration de package | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.configwizard.selectobjects.f1
- sql12.dts.configwizard.selecconfigtype.f1
- sql12.dts.configwizard.finishdtsconfiguration.f1
- sql12.dts.configwizard.welcome.f1
ms.assetid: adca6938-6d5a-40ec-950e-dceb79d044fe
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 8179e5caddbd104fdf35598b7ea25e0f32fd9e84
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84964910"
---
# <a name="package-configuration-wizard-ui-reference"></a>Référence de l'interface utilisateur de l'Assistant Configuration de package
  **L’Assistant Configuration de package** vous permet de créer des configurations chargées de mettre à jour les propriétés d’un package [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ainsi que les objets qui s’y rattachent au moment de l’exécution. Cet Assistant s’exécute quand vous ajoutez une nouvelle configuration ou modifiez une configuration existante dans la boîte de dialogue **Bibliothèque des configurations du package** . Pour ouvrir la boîte de dialogue **Bibliothèque des configurations du package** , sélectionnez **Configurations du package** dans le menu **SSIS** de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Pour plus d’informations, consultez [Créer des configurations de package](../../2014/integration-services/create-package-configurations.md).  
  
> [!NOTE]  
>  Des configurations sont disponibles pour le modèle de déploiement de package. Les paramètres sont utilisés à la place des configurations pour le modèle de déploiement de projet. Le modèle de déploiement de projet vous permet de déployer des projets [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur le serveur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Pour plus d'informations sur les modèles de déploiement, consultez [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).  
  
 Les sections suivantes décrivent les pages de l'Assistant.  
  
## <a name="welcome-to-the-package-configuration-wizard-page"></a>Page Assistant Configuration de package  
 **L’Assistant de configuration de SSIS** vous permet de créer des configurations chargées de mettre à jour les propriétés d’un package ainsi que les objets qui s’y rattachent au moment de l’exécution du programme.  
  
### <a name="options"></a>Options  
 **Ne plus afficher cette page**  
 Option permettant d'ignorer cette page d'accueil la prochaine fois que vous ouvrez l'Assistant.  
  
 **Suivant**  
 Permet de passer à la page suivante de l’Assistant.  
  
## <a name="select-configuration-type-page"></a>Page Sélectionner le type de configuration  
 La page **Sélectionner le type de configuration** permet de spécifier le type de configuration à créer.  
  
 Si vous souhaitez obtenir des informations supplémentaires pour déterminer quel type de configuration utiliser, consultez [Configurations de package](../../2014/integration-services/package-configurations.md).  
  
### <a name="static-options"></a>Options statiques  
 **Type de configuration**  
 Sélectionnez le type de source dans lequel stocker la configuration, à l'aide des options suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|**Fichier de configuration XML**|Stocke la configuration sous forme de fichier XML. Si cette valeur est sélectionnée, les options dynamiques s’affichent dans la section **Type de configuration**.|  
|**Variable d’environnement**|Stocke la configuration dans une des variables d'environnement. Si cette valeur est sélectionnée, les options dynamiques s’affichent dans la section **Type de configuration**.|  
|**Entrée de Registre**|Stocke la configuration dans le Registre. Si cette valeur est sélectionnée, les options dynamiques s’affichent dans la section **Type de configuration**.|  
|**Variable de package parent**|Stocke la configuration en tant que variable dans le package qui contient la tâche.  Si cette valeur est sélectionnée, les options dynamiques s’affichent dans la section **Type de configuration**.|  
|**SQL Server**|Stocke la configuration dans une table de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Si cette valeur est sélectionnée, les options dynamiques s’affichent dans la section **Type de configuration**.|  
  
 **Suivant**  
 Affiche la page suivante de l'Assistant.  
  
### <a name="dynamic-options"></a>Options dynamiques  
  
#### <a name="configuration-type-option--xml-configuration-file"></a>Option Type de configuration = Fichier de configuration XML  
 **Spécifier directement les paramètres de configuration**  
 Permet de spécifier directement les paramètres.  
  
|Value|Description|  
|-----------|-----------------|  
|**Nom du fichier de configuration**|Tapez le chemin d'accès du fichier de configuration généré par l'Assistant.|  
|**Parcourir**|La boîte de dialogue **Sélectionner l’emplacement du fichier de configuration** permet de spécifier le chemin d’accès au fichier de configuration généré par l’Assistant. Si le fichier n'existe pas, l'Assistant le crée.|  
  
 **L'emplacement de la configuration est stocké dans une variable d'environnement**  
 Permet de spécifier la variable d’environnement dans laquelle stocker la configuration.  
  
|Value|Description|  
|-----------|-----------------|  
|**Variable d’environnement**|Permet de sélectionner une variable d'environnement dans la liste.|  
  
#### <a name="configuration-type-option--environment-variable"></a>Option Type de configuration = Variable d'environnement  
 **Variable d’environnement**  
 Permet de sélectionner la variable d'environnement qui contient les informations de configuration.  
  
#### <a name="configuration-type-option--registry-entry"></a>Option Type de configuration = Entrée de Registre  
 **Spécifier directement les paramètres de configuration**  
 Permet de spécifier directement les paramètres.  
  
|Value|Description|  
|-----------|-----------------|  
|**Entrée de Registre**|Tapez la clé de Registre qui contient les informations de configuration. Le format est \<registry key>.<br /><br /> La clé de Registre doit déjà exister dans HKEY_CURRENT_USER et porter une valeur nommée Value. Cette valeur peut être de type DWORD ou une chaîne.<br /><br /> Si vous souhaitez utiliser une clé de Registre qui n’est pas à la racine de HKEY_CURRENT_USER, utilisez le format \<Registry key\registry key\\...> pour identifier la clé.|  
  
 **L'emplacement de la configuration est stocké dans une variable d'environnement**  
 Permet de spécifier la variable d’environnement dans laquelle stocker la configuration.  
  
|Value|Description|  
|-----------|-----------------|  
|**Variable d’environnement**|Permet de sélectionner une variable d'environnement dans la liste.|  
  
#### <a name="configuration-type-option--parent-package-variable"></a>Option Type de configuration = Variable de package parent  
 **Spécifier directement les paramètres de configuration**  
 Permet de spécifier directement les paramètres.  
  
|Value|Description|  
|-----------|-----------------|  
|**Variable parent**|Permet de spécifier la variable dans le package parent qui contient les informations de configuration.|  
  
 **L'emplacement de la configuration est stocké dans une variable d'environnement**  
 Permet de spécifier la variable d’environnement dans laquelle stocker la configuration.  
  
|Value|Description|  
|-----------|-----------------|  
|**Variable d’environnement**|Permet de sélectionner une variable d'environnement dans la liste.|  
  
#### <a name="configuration-type-options--sql-server"></a>Options Type de configuration = SQL Server  
 **Spécifier directement les paramètres de configuration**  
 Permet de spécifier directement les paramètres.  
  
|Value|Description|  
|-----------|-----------------|  
|**Connection**|Permet de sélectionner une connexion dans la liste ou de cliquer sur **Nouvelle** pour créer une connexion.|  
|**Table de configuration**|Permet de sélectionner une table existante ou de cliquer sur **Nouvelle** pour écrire une instruction SQL qui crée une table.|  
|**Filtre de la configuration**|Permet de sélectionner le nom d'une configuration existante ou de taper un nouveau nom.<br /><br /> Un grand nombre de configurations SQL Server peuvent être stockées dans la même table et chacune d'entre elles peut inclure plusieurs éléments de configuration.<br /><br /> La valeur définie par l'utilisateur est stockée dans la table pour identifier les éléments de configuration qui appartiennent à une configuration particulière.|  
  
 **L'emplacement de la configuration est stocké dans une variable d'environnement**  
 Permet de spécifier la variable d'environnement dans laquelle stocker la configuration.  
  
|Value|Description|  
|-----------|-----------------|  
|**Variable d’environnement**|Permet de sélectionner une variable d'environnement dans la liste.|  
  
## <a name="select-objects-to-export-page"></a>Page Sélectionner des objets à exporter  
 Utilisez la page **Sélectionner la propriété cible ou Sélectionner les propriétés à exporter** pour définir les propriétés des objets que contient la configuration. La sélection de plusieurs propriétés n'est possible que si vous sélectionnez le type de configuration XML.  
  
### <a name="options"></a>Options  
 **Objets**  
 Développe la hiérarchie du package et sélectionne les propriétés à exporter.  
  
 **Attributs de la propriété**  
 Affiche les attributs d'une propriété.  
  
 **Suivant**  
 Permet de passer à la page suivante de l'Assistant.  
  
## <a name="completing-the-wizard-page"></a>Page Fin de l’Assistant  
 Utilisez la page **Fin de l’Assistant** pour nommer les paramètres de configuration et d’affichage utilisés par l’Assistant pour créer la configuration. Quand l’Assistant est terminé, la **Bibliothèque des configurations du package** affiche la liste de toutes les configurations du package.  
  
### <a name="options"></a>Options  
 **Nom de la configuration**  
 Tapez le nom de la configuration.  
  
 **Préversion**  
 Affiche les paramètres utilisés par l'Assistant pour créer la configuration.  
  
 **Terminer**  
 Crée la configuration et quitte **l’Assistant Configuration de package**.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des configurations de package](../../2014/integration-services/create-package-configurations.md)  
  
  
