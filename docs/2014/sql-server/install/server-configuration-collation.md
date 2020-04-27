---
title: Configuration du serveur-classement | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- collation configuration, SQL Server
- collation configuration, Setup
- collation configuration
ms.assetid: e3986870-5be4-458b-b671-5ff12a27b022
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 521129056d4513af2f86fb7b70b26621cb881b80
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66092290"
---
# <a name="server-configuration---collation"></a>Configuration du serveur - Classement
  Dans la page Configuration du serveur - Classement de l’Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous pouvez modifier les paramètres de classement utilisés par [!INCLUDE[ssDE](../../includes/ssde-md.md)] et [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour le tri. Sélectionnez l'option pour correspondre aux paramètres de classement de différentes installations de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ou d'un autre ordinateur.  
  
## <a name="options"></a>Options  
 Personnaliser pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit deux groupes de classements : les classements Windows et les classements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez spécifier des paramètres de classement distincts pour le [!INCLUDE[ssDE](../../includes/ssde-md.md)] et [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], ou spécifier le même classement pour les deux.  
  
 Par défaut, un classement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est sélectionné pour les paramètres régionaux système de langue anglaise (US). Le classement par défaut pour les versions localisées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est déterminé par la valeur des paramètres régionaux système Windows pour votre ordinateur.  
  
 Les paramètres par défaut ne doivent être modifiés que si le paramètre de classement de cette installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit se conformer aux paramètres de classement utilisés par une autre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ou aux paramètres régionaux système Windows d'un autre ordinateur.  
  
 **Remarque** [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise uniquement les classements Windows. Si vous envisagez d’installer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], sélectionnez un classement Windows pendant l’exécution du programme d’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin de garantir des résultats cohérents entre le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] et [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Pour plus d'informations, consultez [Paramètres de classement du programme d'installation](https://go.microsoft.com/fwlink/?LinkId=190977).  
  
## <a name="best-practices"></a>Meilleures pratiques  
 Pour plus d’informations sur une table de paramètres régionaux système Windows et les classements par défaut correspondants utilisés par le programme d’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , consultez [Paramètres de classement du programme d’installation](https://go.microsoft.com/fwlink/?LinkId=190977).  
  
 Dans la mesure du possible, choisissez un classement unique pour votre organisation. De cette manière, vous n'avez pas à spécifier explicitement le classement pour chaque base de données, colonne, expression ou identificateur. Si vous devez utiliser plusieurs classements et paramètres de page de codes, codez vos requêtes conformément aux règles de priorité des classements. Pour plus d’informations, consultez la rubrique [Priorité de classement &#40;Transact-SQL&#41;](/sql/t-sql/statements/collation-precedence-transact-sql) dans la documentation en ligne.  
  
 Lorsque vous sélectionnez un classement pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], considérez les recommandations suivantes :  
  
-   Sélectionnez un classement BINARY2 si le classement basé sur les points de code binaires est acceptable.  
  
-   Sélectionnez un classement Windows pour une comparaison cohérente entre les différents types de données.  
  
-   Utilisez le nouveau classement de niveau 100 pour une meilleure prise en charge du tri linguistique. Pour plus d’informations, consultez [Prise en charge d’Unicode et du classement](../../relational-databases/collations/collation-and-unicode-support.md).  
  
-   Si vous prévoyez de migrer une base de données vers l'instance mise à niveau de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sélectionnez le classement qui correspond au classement existant de la base de données.  
  
  
