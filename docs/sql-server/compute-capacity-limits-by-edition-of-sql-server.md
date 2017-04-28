---
title: "Limites de capacité de calcul par édition de SQL Server | Microsoft Docs"
ms.custom: 
ms.date: 06/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- processors [SQL Server], supported
- number of processors supported
- maximum number of processors supported
ms.assetid: cd308bc9-9468-40cc-ad6e-1a8a69aca6c8
caps.latest.revision: 60
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 2f32d9ca838e004676a3cccffbe62bbbc0e46a3f
ms.lasthandoff: 04/11/2017

---
# <a name="compute-capacity-limits-by-edition-of-sql-server"></a>Limites de capacité de calcul par l'édition de SQL Server
  Cette rubrique traite des limites de capacité de calcul des différentes éditions de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] et de la façon dont elles diffèrent dans les environnements physiques et virtualisés avec les processeurs hyperthreaded.  
  
 ![Mappages aux limites de capacité de calcul](../sql-server/media/compute-capacity-limits.gif "Mappages aux limites de capacité de calcul")  
  
 Le tableau suivant décrit les notations utilisées dans le schéma ci-dessus :  
  
|Valeur|Description|  
|-----------|-----------------|  
|0..1|Zéro ou un|  
|1|Un seul|  
|1..*|Un ou plus|  
|0..*|Zéro ou plus|  
|1..2|Un ou deux|  
  
> [!IMPORTANT]  
>  Pour approfondir :  
>   
>  1.  Un ordinateur virtuel est alloué à un ou plusieurs processeurs virtuels.  
> 2.  Un ou plusieurs processeurs virtuels sont alloués à un seul ordinateur virtuel.  
> 3.  Zéro ou un processeur virtuel est mappé à zéro ou un processeur logique. Lorsque le mappage d'un processeur virtuel à un processeur logique est :  
>   
>      -   Un-à-zéro, il représente un processeur logique indépendant non utilisé par les systèmes d'exploitation invités.  
>     -   Un-à-plusieurs, il représente un overcommit.  
>     -   Zéro-à-plusieurs, il représente l'absence d'ordinateur virtuel sur le système hôte, de sorte qu'aucun processeur logique n'est utilisé par les VM.  
> 4.  Un socket est mappé à zéro ou plusieurs noyaux. Lorsque le socket de mappage de noyau est :  
>   
>      -   Un-à-zéro, il représente un socket vide (aucun processeur installé).  
>     -   Un-à-un, il représente un processeur à un noyau installé dans le socket (très rare de nos jours).  
>     -   Un-à-plusieurs, il représente un processeur à plusieurs noyaux installé dans le socket (les valeurs courantes sont 2,4,8).  
> 5.  Un noyau est mappé à un ou deux processeurs logiques. Lorsque le mappage du noyau au processeur logique est :  
>   
>      -   Un-à-un, l'hyperthreading est désactivé.  
>     -   Un-à-deux, l'hyperthreading est activé.  
  
 Les définitions suivantes s'appliquent aux termes utilisés dans cette rubrique :  
  
-   Un thread ou un processeur logique est un moteur de calcul logique du point de vue de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], du système d'exploitation, d'une application ou du pilote.  
  
-   Un noyau est une unité de processeur, qui peut comprendre un ou plusieurs processeurs logiques.  
  
-   Un processeur physique peut comprendre un ou plusieurs noyaux. Un processeur physique est identique à un package de processeurs ou à un socket.  
  
 Les systèmes avec plusieurs processeurs physiques ou avec des processeurs physiques qui ont plusieurs noyaux et/ou des hyperthreads, permettent au système d'exploitation d'exécuter plusieurs tâches simultanément. Chaque thread d'exécution apparaît comme un processeur logique. Par exemple, si vous avez un ordinateur qui a deux processeurs quadruple cœur avec des threads activés et deux threads par noyau, vous avez 16 processeurs logiques : 2 processeurs X les 4 cœurs par processeur X 2 thread par cœur. Il faut noter que :  
  
-   La capacité de calcul d'un processeur logique à partir d'un thread unique d'un noyau hyperthreaded est inférieure à la capacité de calcul d'un processeur logique de ce même noyau avec l'hyperthreading désactivé.  
  
-   Cependant, la capacité de calcul des 2 processeurs logiques dans le noyau hyperthreaded est supérieure à la capacité de calcul du même noyau avec l'hyperthreading désactivé.  
  
 Chaque édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] a deux limites de capacité de calcul :  
  
1.  Un nombre maximal de sockets (identique au processeur physique ou au socket ou au package de processeurs).  
  
2.  Un nombre maximum de noyaux comme indiqué par le système d'exploitation.  
  
 Ces limites s'appliquent à une seule instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Elles représentent la capacité maximale de calcul qu'une seule instance utilise. Elles ne limitent pas le serveur sur lequel l'instance peut être déployée. En fait, le déploiement de plusieurs instances de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur le même serveur physique est un moyen efficace d'utiliser la capacité de calcul d'un serveur physique avec plus de sockets et/ou de noyaux que les limites de capacité ci-dessous.  
  
 Le tableau suivant présente les limites de capacité de calcul pour une instance unique de chaque édition de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]:  
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Édition|Capacité maximale de calcul utilisée par une instance unique ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../includes/ssde-md.md)])|Capacité maximale de calcul utilisée par une instance unique (AS, RS)|  
|---------------------------------------|--------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------|  
|Enterprise Edition : contrat de licence selon le nombre de cœurs*|Maximum du système d'exploitation|Maximum du système d'exploitation|  
|Développeur|Maximum du système d'exploitation|Maximum du système d'exploitation|  
|Standard|Limité à moins de 4 sockets ou 24 cœurs|Limité à moins de 4 sockets ou 24 cœurs|  
|Express|Limité à moins de 1 socket ou 4 cœurs|Limité à moins de 1 socket ou 4 cœurs|  
 *Enterprise Edition avec serveur + licences d’accès client (CAL) (non disponibles pour les nouveaux contrats) limitées à un maximum de 20 cœurs par instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Il n'existe aucune limite dans le mode de licence Serveur selon le nombre de cœurs.  
  
 Dans un environnement virtualisé, la limite de capacité de calcul est basée sur le nombre de processeurs logiques et non de noyaux, car l'architecture du processeur n'est pas visible aux applications invitées.  Par exemple, un serveur avec quatre sockets comprenant des processeurs quadruple cœur et autorisant l'activation de deux hyperthreads par cœur, contient 32 processeurs logiques avec l'hyperthreading activé mais seulement 16 processeurs logiques avec l'hyperthreading désactivé. Ces processeurs logiques peuvent être mappés aux ordinateurs virtuels sur le serveur avec la charge du calcul des ordinateurs virtuels, sur ce processeur logique mappé sur un thread d'exécution sur le processeur physique dans le serveur hôte.  
  
 Vous pouvez désactiver l'hyperthreading lorsque les performances par processeur virtuel sont importantes. Vous pouvez activer ou désactiver l'hyperthreading sur le processeur à l'aide d'un paramètre du BIOS pendant l'installation de celui-ci, mais il s'agit en général d'une opération couvrant l'étendue du serveur qui aura un impact sur toutes les charges de travail qui s'exécutent sur le serveur. On peut dans ce cas suggérer la séparation des charges de travail qui s'exécutent dans des environnements virtualisés de celles qui tirent parti de l'amélioration des performances grâce à l'hyperthreading dans un environnement de système d'exploitation physique.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditions et composants de SQL Server 2016](../sql-server/editions-and-components-of-sql-server-2016.md)   
 [Fonctionnalités prises en charge par les éditions de SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)   
 [Spécifications des capacités maximales pour SQL Server](../sql-server/maximum-capacity-specifications-for-sql-server.md)   
 [Installation de démarrage rapide de SQL Server 2016](http://msdn.microsoft.com/library/672afac9-364d-4946-ad5d-8a2d89cf8d81)  
  
  


