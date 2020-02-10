---
title: Bibliothèque de configurations du package | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.packageconfigurationorganizer.f1
helpviewer_keywords:
- Package Configurations Organizer dialog box
ms.assetid: f20ae6cb-9e6a-4d24-88ff-d7a903a4e8d3
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d5313118f7949818d341a47744a69cf13c43dbc9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66056964"
---
# <a name="package-configurations-organizer"></a>Bibliothèque des configurations du package
  Utilisez la boîte de dialogue **Bibliothèque des configurations du package** pour activer les configurations du package, afficher une liste des configurations du package actuel et spécifier l'ordre de chargement de préférence des configurations.  
  
> [!NOTE]  
>  Des configurations sont disponibles pour le modèle de déploiement de package. Les paramètres sont utilisés à la place des configurations pour le modèle de déploiement de projet. Le modèle de déploiement de projet vous permet de déployer des projets [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur le serveur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Pour plus d'informations sur les modèles de déploiement, consultez [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).  
  
 Si plusieurs configurations mettent à jour la même propriété, les valeurs des configurations du bas de la liste de configuration remplacent les valeurs des configurations du haut de la liste. La dernière valeur chargée dans la propriété est la valeur utilisée à l'exécution du package. De plus, si le package utilise une combinaison de configuration directe (par exemple, un fichier de configuration XML) et de configuration indirecte (par exemple, une variable d'environnement), la configuration indirecte qui pointe vers l'emplacement de la configuration directe doit figurer plus haut dans la liste.  
  
> [!NOTE]  
>  Lorsque les configurations du package sont chargées dans l'ordre souhaité, le chargement est effectué du haut vers le bas de la liste affichée dans la boîte de dialogue **Bibliothèques des configurations du package** . Toutefois, au moment de l'exécution, il se peut que les configurations de package ne soient pas chargées dans l'ordre souhaité. Les configurations de package parent sont notamment chargées après les configurations d'autres types.  
  
 Les configurations de package mettent à jour les valeurs des propriétés des objets de package au moment de l'exécution. Lorsqu'un package est chargé, les valeurs des configurations remplacent les valeurs définies lors du développement du package. 
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] prend en charge différents types de configuration. Par exemple, vous pouvez utiliser un fichier XML pouvant contenir plusieurs configurations, ou une variable d'environnement qui contient une seule configuration. Pour plus d’informations, consultez [Package Configurations](../../2014/integration-services/package-configurations.md).  
  
## <a name="options"></a>Options  
 **Activer les configurations de package**  
 Sélectionnez cette option pour utiliser les configurations avec le package.  
  
 **Nom de la configuration**  
 Affichez le nom de la configuration.  
  
 **Type de configuration**  
 Affichez le type de l'emplacement où sont stockées les configurations.  
  
 **Chaîne de configuration**  
 Affichez l'emplacement où sont stockées les valeurs de configuration. L'emplacement peut être le chemin d'accès d'un fichier, le nom d'une variable d'environnement, le nom d'une variable de package parent, une clé de Registre ou le nom d'une table [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 **Objet cible**  
 Affiche le nom de l'objet mis à jour par la configuration. Si la configuration est un fichier de configuration XML ou une table SQL Server, la colonne est vide puisque la configuration peut inclure plusieurs objets.  
  
 **Propriété cible**  
 Affichez le nom de la propriété modifiée par la configuration. Cette colonne est vide si le type de configuration prend en charge plusieurs configurations.  
  
 **Ajouter**  
 Ajoutez une configuration à l'aide de l'Assistant Configuration de package.  
  
 **Modifier**  
 Modifiez une configuration existante en réexécutant l'Assistant Configuration de package.  
  
 **Remove**  
 Sélectionnez une configuration, puis cliquez sur **Supprimer**.  
  
 **Situées**  
 Sélectionnez une configuration et utilisez les flèches vers le haut et vers le bas pour la déplacer vers le haut ou vers le bas de la liste. Les configurations sont chargées dans l'ordre dans lequel elles apparaissent dans la liste.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des configurations de package](../../2014/integration-services/create-package-configurations.md)  
  
  
