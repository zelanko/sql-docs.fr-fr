---
title: Configuration de l’instance | Microsoft Docs
ms.custom: ''
ms.date: 2016-05-04
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- instance configuration, Setup
helpviewer_keywords:
- Instance Name page [SQL Server Installation Wizard]
- SQL Server Installation Wizard, Instance Name page
ms.assetid: 5bf822fc-6dec-4806-a153-e200af28e9a5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5008096ef5c10dbd3f14198194cec4e7795d9f4a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48202309"
---
# <a name="instance-configuration"></a>Configuration de l'instance
  Utilisez la page **Configuration d’une instance** de l’Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour spécifier s’il faut créer une instance par défaut ou une instance nommée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’est pas déjà installée, une instance par défaut est créée, sauf si vous spécifiez une instance nommée.  
  
 Chaque instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consiste en un ensemble distinct de services avec des paramètres spécifiques pour les classements et les autres options. La structure des répertoires, la structure du Registre et les noms de services reflètent tous le nom de l'instance et l'ID spécifique de l'instance créé durant l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Une instance est soit l'instance par défaut, soit une instance nommée. MSSQLSERVER est le nom de l'instance par défaut. Il n'est pas nécessaire qu'un client spécifie le nom de l'instance pour établir une connexion. Une instance nommée est déterminée par l'utilisateur au cours de l'installation. Vous pouvez installer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] comme instance nommée sans installer d'abord l'instance par défaut. Une seule installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], indépendamment de la version, peut être à un instant donné l'instance par défaut.  
  
 **Alerte !** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep vous permet de spécifier le nom de l’instance quand vous finalisez une instance préparée dans la page **Configuration de l’instance**. Vous pouvez choisir de configurer l'instance préparée que vous finalisez comme instance par défaut s'il n'existe aucune instance par défaut de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur l'ordinateur.  
  
## <a name="multiple-instances"></a>Instances multiples  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un seul serveur ou processeur, mais une seule instance peut être l'instance par défaut. Toutes les autres instances doivent être des instances nommées. Un ordinateur peut exécuter simultanément plusieurs instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et chaque instance s'exécute indépendamment des autres.  
  
 Pour plus d’informations, consultez [Spécifications des capacités maximales pour SQL Server](../maximum-capacity-specifications-for-sql-server.md).  
  
## <a name="options"></a>Options  
 Instances de cluster de basculement uniquement : Spécifiez le nom réseau du cluster de basculement de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ce nom identifie l'instance de cluster de basculement sur le réseau.  
  
 Instance par défaut ou instance nommée — Prenez ces informations en compte lorsque vous décidez d'installer une instance par défaut ou une instance nommée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   Si vous envisagez d'installer une seule instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un serveur de bases de données, ce doit être une instance par défaut.  
  
-   Utilisez une instance nommée lorsque vous envisagez plusieurs instances sur le même ordinateur. Un serveur ne peut héberger qu'une seule instance par défaut.  
  
-   Toute application qui installe [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] doit l'installer en tant qu'instance nommée. Ce procédé réduit au minimum les conflits liés à l'installation de plusieurs applications sur le même ordinateur.  
  
 **Instance par défaut**  
 Choisissez cette option pour installer une instance par défaut de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Un ordinateur ne peut héberger qu'une instance par défaut ; toutes les autres instances doivent être nommées. Toutefois, si vous avez une instance par défaut de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installée, vous pouvez ajouter une instance par défaut de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sur le même ordinateur.  
  
 **Instance nommée**  
 Sélectionnez cette option pour créer une nouvelle instance nommée. Prenez en compte les points suivants lorsque vous nommez une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   Les noms d'instance ne respectent pas la casse.  
  
-   Les noms d'instance ne peuvent pas commencer ni se terminer par un trait de soulignement (_).  
  
-   Les noms d'instance ne peuvent pas contenir le terme « Default » ou autres mots clés réservés. Si un mot clé réservé est utilisé dans le nom d'une instance, une erreur d'installation se produit. Pour plus d’informations, consultez [Mots clés réservés &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reserved-keywords-transact-sql).  
  
-   Si vous spécifiez MSSQLServer comme nom d'instance, une instance par défaut est créée.  
  
-   Une installation de [!INCLUDE[ssGeminiLong](../../includes/ssgeminilong-md.md)] est toujours installée comme instance nommée de « PowerPivot ». Vous ne pouvez pas spécifier de nom d'instance différent pour ce rôle de fonctionnalité.  
  
-   Les noms d'instance sont limités à 16 caractères.  
  
-   Le premier caractère d'un nom d'instance doit être une lettre. Les lettres acceptables sont celles définies par la norme Unicode 2.0. Elles incluent les caractères latins a-z, A-Z et les caractères littéraux des autres langues.  
  
-   Les autres caractères d'un nom d'instance peuvent être des lettres définies par le standard Unicode 2.0, des nombres décimaux provenant de scripts de latin de base ou nationaux, le symbole dollar ($) ou le trait de soulignement (_).  
  
-   Les espaces incorporés ou autres caractères spéciaux ne sont pas autorisés dans les noms d'instance. La barre oblique inverse (\\), la virgule (,), le deux-points (:), le point-virgule (;), le guillemet simple ('), l’esperluette (&) et l’arobase (@) ne sont pas autorisés non plus.  
  
-   **Uniquement des caractères qui sont valides dans la page de codes Windows actuelle peuvent être utilisés dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] noms d’instance. Si un caractère Unicode non pris en charge est utilisé, une erreur se produit.**  
  
 **Instances et fonctionnalités détectées**  
 Consultez la liste des instances et des composants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installés sur l'ordinateur sur lequel le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en cours d'exécution.  
  
 **ID d’instance** : Par défaut, le nom de l’instance est utilisé comme ID d’instance. Il permet d'identifier les répertoires d'installation et les clés de Registre de votre instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Tel est le cas pour les instances par défaut et les instances nommées. Pour une instance par défaut, le nom de l'instance et l'ID d'instance sont MSSQLSERVER. Pour utiliser un ID d’instance non défini par défaut, spécifiez-le dans le champ **ID d’instance** .  
  
> [!IMPORTANT]  
>  Avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep, l'ID d'instance affiché dans cette page correspond à l'ID d'instance spécifié pendant l'étape de préparation d'image du processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep. Vous ne serez pas en mesure de spécifier un ID d'instance différent pendant l'étape de finalisation d'image.  
  
> [!NOTE]  
>  Les ID d'instance qui commencent par un trait de soulignement (_) ou qui contiennent le signe dièse (#) ou le symbole dollar ($) ne sont pas pris en charge.  
  
 Pour plus d’informations sur les répertoires, les emplacements de fichiers et l’affectation de noms aux ID d’instance, consultez [Emplacements des fichiers pour les instances par défaut et les instances nommées de SQL Server](../../../2014/sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md).  
  
 Tous les composants d'une instance donnée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont gérés comme une unité. Tous les Service Packs et mises à niveau [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'appliqueront à chaque composant d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Tous les composants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui partagent le même nom d'instance doivent remplir les critères suivants :  
  
-   **Même version**  
  
-   **Même édition**  
  
-   **Mêmes paramètres de langue**  
  
-   **Même état cluster**  
  
    > [!NOTE]  
    >  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] n’est pas sensible aux clusters.  
  
-   **Même système d’exploitation**  
  
  
