---
title: "Biblioth&#232;que des configurations du package | Microsoft Docs"
ms.custom: ""
ms.date: "08/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.packageconfigurationorganizer.f1"
helpviewer_keywords: 
  - "Bibliothèque des configurations du package, boîte de dialogue"
ms.assetid: f20ae6cb-9e6a-4d24-88ff-d7a903a4e8d3
caps.latest.revision: 39
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 39
---
# Biblioth&#232;que des configurations du package
  Utilisez la boîte de dialogue **Bibliothèque des configurations du package** pour activer les configurations du package, afficher une liste des configurations du package actuel et spécifier l'ordre de chargement de préférence des configurations.  
  
> **REMARQUE :** des configurations sont disponibles pour le modèle de déploiement de package. Les paramètres sont utilisés à la place des configurations pour le modèle de déploiement de projet. Le modèle de déploiement de projet vous permet de déployer des projets [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Pour plus d'informations sur les modèles de déploiement, consultez [Deployment of Projects and Packages](https://msdn.microsoft.com/library/hh213290.aspx).  
  
 Si plusieurs configurations mettent à jour la même propriété, les valeurs des configurations du bas de la liste de configuration remplacent les valeurs des configurations du haut de la liste. La dernière valeur chargée dans la propriété est la valeur utilisée à l'exécution du package. De plus, si le package utilise une combinaison de configuration directe (par exemple, un fichier de configuration XML) et de configuration indirecte (par exemple, une variable d'environnement), la configuration indirecte qui pointe vers l'emplacement de la configuration directe doit figurer plus haut dans la liste.  
  
> **REMARQUE :** lorsque les configurations du package sont chargées dans l’ordre souhaité, le chargement est effectué du haut vers le bas de la liste affichée dans la boîte de dialogue **Bibliothèques des configurations du package** . Toutefois, au moment de l'exécution, il se peut que les configurations de package ne soient pas chargées dans l'ordre souhaité. Les configurations de package parent sont notamment chargées après les configurations d'autres types.  
  
 Les configurations de package mettent à jour les valeurs des propriétés des objets de package au moment de l'exécution. Lorsqu'un package est chargé, les valeurs des configurations remplacent les valeurs définies lors du développement du package. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] prend en charge différents types de configuration. Par exemple, vous pouvez utiliser un fichier XML pouvant contenir plusieurs configurations, ou une variable d'environnement qui contient une seule configuration. Pour plus d'informations, consultez [Package Configurations](../../integration-services/packages/package-configurations.md).  
  
## Options  
 **Activer les configurations du package**  
 Sélectionnez cette option pour utiliser les configurations avec le package.  
  
 **Nom de la configuration**  
 Affichez le nom de la configuration.  
  
 **Type de configuration**  
 Affichez le type de l'emplacement où sont stockées les configurations.  
  
 **Chaîne de configuration**  
 Affichez l'emplacement où sont stockées les valeurs de configuration. L'emplacement peut être le chemin d'accès d'un fichier, le nom d'une variable d'environnement, le nom d'une variable de package parent, une clé de Registre ou le nom d'une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Objet cible**  
 Affiche le nom de l'objet mis à jour par la configuration. Si la configuration est un fichier de configuration XML ou une table SQL Server, la colonne est vide puisque la configuration peut inclure plusieurs objets.  
  
 **Propriété cible**  
 Affichez le nom de la propriété modifiée par la configuration. Cette colonne est vide si le type de configuration prend en charge plusieurs configurations.  
  
 **Ajouter**  
 Ajoutez une configuration à l'aide de l'Assistant Configuration de package.  
  
 **Modifier**  
 Modifiez une configuration existante en réexécutant l'Assistant Configuration de package.  
  
 **Supprimer**  
 Sélectionnez une configuration, puis cliquez sur **Supprimer**.  
  
 **Flèches**  
 Sélectionnez une configuration et utilisez les flèches vers le haut et vers le bas pour la déplacer vers le haut ou vers le bas de la liste. Les configurations sont chargées dans l'ordre dans lequel elles apparaissent dans la liste.  
  
## Voir aussi  
 [Créer des configurations de package](../../integration-services/packages/create-package-configurations.md)  
  
  