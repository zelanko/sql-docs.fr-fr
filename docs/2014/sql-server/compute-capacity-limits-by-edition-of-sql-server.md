---
title: Limites de capacité de calcul par édition de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- processors [SQL Server], supported
- number of processors supported
- maximum number of processors supported
ms.assetid: cd308bc9-9468-40cc-ad6e-1a8a69aca6c8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f457c901c4226b9a0ead23de57c2455c619f406e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62714760"
---
# <a name="compute-capacity-limits-by-edition-of-sql-server"></a>Limites de capacité de calcul par l'édition de SQL Server
  Cette rubrique traite des limites de capacité de calcul des différentes éditions de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] et de la façon dont elles diffèrent dans les environnements physiques et virtualisés avec les processeurs hyperthreaded.  
  
 ![Mappages aux limites de capacité de calcul](../../2014/getting-started/media/compute-capacity-limits.gif "Mappages aux limites de capacité de calcul")  
  
 Le tableau suivant décrit les notations utilisées dans le schéma ci-dessus :  
  
|Valeur|Description|  
|-----------|-----------------|  
|0..1|Zéro ou un|  
|1|Un seul|  
|1..*|Un ou plus|  
|0..*|Zéro ou plus|  
|1..2|Une ou deux|  
  
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
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Édition|Capacité maximale de calcul utilisée par une instance unique ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../includes/ssde-md.md)])|Capacité maximale de calcul utilisée par une instance unique (AS, RS)|  
|---------------------------------------|--------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------|  
|Enterprise Edition : licence basée sur le cœur<sup>1</sup>|Maximum du système d'exploitation|Maximum du système d'exploitation|  
|Développeur|Maximum du système d'exploitation|Maximum du système d'exploitation|  
|Évaluation|Maximum du système d'exploitation|Maximum du système d'exploitation|  
|Business Intelligence|Limité inférieure à 4 sockets ou 16 noyaux|Maximum du système d'exploitation|  
|standard|Limité inférieure à 4 sockets ou 16 noyaux|Limité inférieure à 4 sockets ou 16 noyaux|  
|Web|Limité inférieure à 4 sockets ou 16 noyaux|Limité inférieure à 4 sockets ou 16 noyaux|  
|Express|Limité inférieure à 1 sockets ou 4 noyaux|Limité inférieure à 1 sockets ou 4 noyaux|  
|Express with Tools|Limité inférieure à 1 sockets ou 4 noyaux|Limité inférieure à 1 sockets ou 4 noyaux|  
|Express with Advanced Services|Limité inférieure à 1 sockets ou 4 noyaux|Limité inférieure à 1 sockets ou 4 noyaux|  
  
 <sup>1</sup> Enterprise Edition avec serveur + licences d’accès client (CAL) (non disponibles pour les nouveaux contrats) est limitée à un maximum de 20 cœurs par [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance. Il n'existe aucune limite dans le mode de licence Serveur selon le nombre de cœurs.  
  
 Dans un environnement virtualisé, la limite de capacité de calcul est basée sur le nombre de processeurs logiques et non de noyaux, car l'architecture du processeur n'est pas visible aux applications invitées.  Par exemple, un serveur avec quatre sockets comprenant des processeurs quadruple cœur et autorisant l'activation de deux hyperthreads par cœur, contient 32 processeurs logiques avec l'hyperthreading activé mais seulement 16 processeurs logiques avec l'hyperthreading désactivé. Ces processeurs logiques peuvent être mappés à des ordinateurs virtuels sur le serveur avec la charge de calcul des machines virtuelles sur ce processeur logique mappé dans un thread d’exécution sur le processeur physique dans le serveur hôte.  
  
 Vous pouvez désactiver l'hyperthreading lorsque les performances par processeur virtuel sont importantes. Vous pouvez activer ou désactiver l'hyperthreading sur le processeur à l'aide d'un paramètre du BIOS pendant l'installation de celui-ci, mais il s'agit en général d'une opération couvrant l'étendue du serveur qui aura un impact sur toutes les charges de travail qui s'exécutent sur le serveur. On peut dans ce cas suggérer la séparation des charges de travail qui s'exécutent dans des environnements virtualisés de celles qui tirent parti de l'amélioration des performances grâce à l'hyperthreading dans un environnement de système d'exploitation physique.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditions et composants de SQL Server 2014](../sql-server/editions-and-components-of-sql-server-2016.md)   
 [Fonctionnalités prises en charge par les éditions de SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Spécifications de capacité maximale pour SQL Server](../sql-server/maximum-capacity-specifications-for-sql-server.md)   
 [Installation de démarrage rapide de SQL Server 2014](../../2014/getting-started/quick-start-installation-of-sql-server-2014.md)  
  
  
