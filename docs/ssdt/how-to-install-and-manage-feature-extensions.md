---
title: 'Procédure : installer et gérer des extensions de fonctionnalités | Microsoft Docs'
ms.custom:
- SSDT
ms.date: 04/26/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 9cdc8cd5-c36f-4bee-a191-87ed457803e7
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 3240bd208a13342782fefeb19532fbabed7e81e1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65099685"
---
# <a name="how-to-install-and-manage-feature-extensions"></a>Procédure : Installer et gérer des extensions de fonctionnalités
Il est possible d’ajouter des règles d’analyse du code de la base de données, des conditions pour les tests unitaires de base de données et des contributeurs Build and Deployment pour améliorer les fonctionnalités offertes par les différentes éditions de Visual Studio, y compris SQL Server Data Tools. Cependant, vous devrez tout d’abord installer l’extension de fonctionnalité pour pouvoir l’utiliser, qu’elle ait été créée par vous ou par quelqu’un d’autre.  
  
L'endroit où vous installerez votre extension dépend du type d'extension et de l'emplacement d'utilisation. Dans les dernières éditions de Visual Studio, l’emplacement d’installation de certains composants n’est plus le répertoire d’installation de SQL Server, mais le répertoire Visual Studio. Grâce à cette configuration, il est plus facile d’exécuter côte à côte différentes versions du logiciel, mais cela signifie aussi qu’il peut être nécessaire d’installer l’extension à plusieurs emplacements pour pouvoir l’utiliser dans différentes versions de SQL Server Data Tools et en ligne de commande.  
  
### <a name="installing-extensions-for-use-inside-visual-studio"></a>Installer des extensions pour une utilisation dans Visual Studio  
  
|Type d'extension|Emplacement d’installation|  
|------------------|--------------------|  
|Condition de test personnalisée pour les tests unitaires SQL Server|<Visual Studio Install Dir>\Common7\IDE\Extensions\\Microsoft\SQLDB\TestConditions|  
|Collaborateurs de build<br /><br />Collaborateurs de déploiement<br /><br />Règles d'analyse statique du code|<Visual Studio Install Dir>\Common7\IDE\Extensions\\Microsoft\SQLDB\DAC\120\Extensions|  
  
<Visual Studio Install Dir> dépend de la version de Visual Studio utilisée et de l’emplacement d’installation choisi. Pour Visual Studio 2012, il s’agit généralement de C:\Program Files (x86)\\MicrosoftVisual Studio 11.0. Pour Visual Studio 2013, il s’agit généralement de C:\Program Files (x86)\\MicrosoftVisual Studio 12.0.  
  
Les extensions peuvent être exécutées dans le cadre de nos services de ligne de commande :  
  
|Type d'extension|Service de ligne de commande|Dossier d'installation|  
|------------------|------------------------|------------------|  
|Condition de test personnalisée pour les tests unitaires SQL Server|MSBuild/MSTest peut être utilisé pour exécuter des tests unitaires dans l’Invite de commandes développeur de Visual Studio 2013 et avec des outils en ligne de commande similaires.|Le même qu’en cas d’exécution dans Visual Studio.|  
|Collaborateurs de build<br /><br />Collaborateurs de déploiement|[SqlPackage.exe](../tools/sqlpackage.md), ou à l’aide de cibles de déploiement ou de publication MSBuild lors de la génération d’un projet de base de données.|MSBuild : Le même qu’en cas d’exécution dans Visual Studio.<br /><br />[SqlPackage.exe](../tools/sqlpackage.md) : s’il se trouve dans le répertoire Visual Studio, le même qu’avant.<br /><br />Si SqlPackage.exe et d’autres DLL DacFx se trouvent en dehors de ce répertoire, les extensions doivent être placées dans le même répertoire ou dans C:\Program Files (x86)\\MicrosoftSQL Server\120\DAC\bin\Extensions.|  
|Règles d'analyse statique du code|Vous pouvez utiliser MSBuild pour générer le projet et exécuter l'analyse statique du code.<br /><br />Vous pouvez de plus exécuter l’analyse du code avec une API CodeAnalysisService dans vos propres applications. Dans ce cas, les règles de recherche d'extension fonctionnent comme lors de l'utilisation de SqlPackage.exe.|Le même que pour les collaborateurs de déploiement et de génération.|  
  
> [!NOTE]  
> Vous devez avoir des autorisations d'administrateur sur votre ordinateur pour accéder aux répertoires d'installation sous le dossier Program Files. Si vous n'avez pas les autorisations appropriées, contactez votre administrateur réseau.  
  
**Considérations relatives à la sécurité**  
  
Avant d’installer une extension dont vous n’êtes pas l’auteur, prenez connaissance des risques suivants :  
  
-   Le programme d’installation de l’extension peut être malveillant et, selon vos autorisations d’installation, accéder à des ressources protégées.  
  
-   L’extension peut être elle-même malveillante et prendre le contrôle de ressources protégées si l’utilisateur qui s’en sert dispose des autorisations nécessaires.  
  
Pour réduire le risque, n’installez l’extension que si elle provient d’une source connue. Si elle est issue d’une source non approuvée, examinez son code source et son programme d’installation (le cas échéant) avant de l’installer et de l’utiliser.  
  
## <a name="to-install-a-custom-feature-extension"></a>Pour installer une extension de fonctionnalité personnalisée  
Copiez l'assembly signé (.dll) dans le dossier d'installation correct. Fermez et rouvrez Visual Studio. L'extension doit maintenant être disponible.  
  
## <a name="see-also"></a>Voir aussi  
[Extension des fonctionnalités de base de données](../ssdt/extending-the-database-features.md)  
  
