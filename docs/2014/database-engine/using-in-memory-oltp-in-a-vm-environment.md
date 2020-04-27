---
title: Utilisation de l’OLTP en mémoire dans un environnement de machine virtuelle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 27ec7eb3-3a24-41db-aa65-2f206514c6f9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e7f7f04b04792167fe9c4733f3e066c362f3cae4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62843058"
---
# <a name="using-in-memory-oltp-in-a-vm-environment"></a>Utilisation de l’OLTP en mémoire dans un environnement de machine virtuelle
  La virtualisation de serveur vous permet de réduire les coûts d’exploitation et de capital informatique et d’optimiser l’efficacité informatique, grâce à des processus de configuration, de maintenance, de disponibilité, de sauvegarde et de récupération d’applications optimisés. Avec les progrès technologiques récents, les charges de travail de base de données complexes peuvent être consolidées plus aisément à l'aide de la virtualisation. Cette rubrique porte sur les meilleures pratiques relatives à l’utilisation de [!INCLUDE[hek_1](../includes/hek-1-md.md)] dans un environnement virtualisé.  
  
##  <a name="memory-pre-allocation"></a><a name="bkmk_memoryPreAllocation"></a>Pré-allocation de mémoire  
 Pour la mémoire dans un environnement virtualisé, de meilleures performances et une prise en charge améliorée sont essentielles. Vous devez pouvoir allouer rapidement de la mémoire aux machines virtuelles en fonction des exigences (charges de pointe et creuses) et garantir que la mémoire n'est pas gaspillée. La fonctionnalité de mémoire dynamique d’Hyper-V augmente l’agilité de l’allocation et de la gestion de la mémoire entre les machines virtuelles exécutées sur un hôte.  
  
 Certains meilleures pratiques pour virtualiser et gérer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ont besoin d'être modifiées lors de la virtualisation d'une base de données avec des tables mémoire optimisées. Sans les tables mémoire optimisées, les deux meilleures pratiques sont les suivantes :  
  
-   Si vous utilisez le paramètre MIN_SERVER_MEMORY, il vaut mieux allouer uniquement la quantité de mémoire nécessaire, afin qu’une mémoire suffisante reste disponible pour d’autres processus (évitant ainsi la pagination).  
  
-   Ne définissez pas la préallocation de mémoire sur une valeur trop élevée. Sinon, les autres processus ne disposeront pas de suffisamment de mémoire au moment où ils en ont besoin, ce qui peut entraîner une pagination de mémoire.  
  
 Si vous suivez les pratiques ci-dessus pour une base de données avec des tables à mémoire optimisée, une tentative de récupération et de restauration d’une base de données peut entraîner le blocage de la base de données à l’état « Récupération en attente », même si vous avez suffisamment de mémoire disponible pour la récupérer. En effet, au démarrage, [!INCLUDE[hek_2](../includes/hek-2-md.md)] met les données en mémoire plus rapidement que l’allocation de mémoire dynamique n’alloue la mémoire nécessaire à la base de données.  
  
 **Résolution :**  
  
 Pour atténuer ce problème, préallouez suffisamment de mémoire à la base de données pour la récupération ou le redémarrage ; ne vous contentez pas d'une valeur minimale en comptant sur la mémoire dynamique pour fournir la mémoire supplémentaire lorsque cela est nécessaire.  
  
## <a name="see-also"></a>Voir aussi  
 [OLTP en mémoire &#40;optimisation en mémoire&#41;](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
