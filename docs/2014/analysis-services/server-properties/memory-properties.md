---
title: Propriétés de mémoire | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- LowMemoryLimit property
- MinimumAllocatedMemory property
- MidMemoryPrice property
- MemoryHeapType property
- memory [Analysis Services]
- DefaultPagesCountToReuse property
- TotalMemoryLimit property
- SessionMemoryLimit property
- VirtualMemoryLimit property
- WaitCountIfHighMemory property
- HighMemoryPrice property
- HeapTypeForObjects property
ms.assetid: 085f5195-7b2c-411a-9813-0ff5c6066d13
caps.latest.revision: 22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 77902cfe21cf2f486007f802c0556bd410f46d4e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37286375"
---
# <a name="memory-properties"></a>Propriétés de mémoire
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prend en charge les propriétés de mémoire du serveur répertoriées dans le tableau suivant. Pour obtenir des conseils sur la définition de ces propriétés, consultez le [guide des opérations de SQL Server 2008 R2 Analysis Services](http://go.microsoft.com/fwlink/?LinkID=225539).  
  
 Les valeurs comprises entre 1 et 100 représentent des pourcentages de **mémoire physique totale** ou d' **espace d'adressage virtuel**, la valeur la plus petite étant retenue. Les valeurs supérieures à 100 représentent les limites de mémoire en octets.  
  
 **S'applique à :** mode serveur multidimensionnel et tabulaire, sauf indication contraire.  
  
## <a name="properties"></a>Propriétés  
 `LowMemoryLimit`  
 Une propriété de nombre signé 64 bits à virgule flottante double précision qui définit le point auquel le serveur manque de mémoire, exprimée en pourcentage de mémoire physique totale. Lorsque cette limite est atteinte, l'instance commence lentement à nettoyer la mémoire des caches en fermant les sessions expirées et en déchargeant les calculs non utilisés. Le serveur ne libère pas la mémoire en dessous de cette limite. La valeur par défaut est 65, ce qui indique que la limite de mémoire inférieure correspond à 65 % de la mémoire physique ou de l'espace d'adressage virtuel, la valeur inférieure étant applicable.  
  
 `TotalMemoryLimit`  
 Définit un seuil qui, une fois atteint, a pour effet d'indiquer au serveur de désallouer la mémoire de façon intensive. La valeur par défaut est 80 % de la mémoire physique ou de l'espace d'adressage virtuel, la valeur inférieure étant applicable.  
  
 Notez que `TotalMemoryLimit` doit toujours être inférieur à `HardMemoryLimit`.  
  
 `HardMemoryLimit`  
 Spécifie un seuil de mémoire après lequel l'instance ferme de façon intensive les sessions utilisateur actives pour réduire l'utilisation de la mémoire. Toutes les sessions fermées vont générer une erreur relative à l'annulation par sollicitation de la mémoire. La valeur par défaut, zéro (0) signifie que le `HardMemoryLimit` définira une valeur intermédiaire entre `TotalMemoryLimit` et la mémoire physique totale du système ; si la mémoire physique du système est supérieure à l’espace d’adressage virtuel de l’adresse de processus, puis virtuel espace sera utilisé à la place pour calculer `HardMemoryLimit`.  
  
 `VirtualMemoryLimit`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `VertiPaqPagingPolicy`  
 Spécifie le comportement de pagination lorsque le serveur est à court de mémoire. Les valeurs valides sont les suivantes :  
  
 Zéro (**0**) désactive la pagination. Si la mémoire est insuffisante, le traitement échoue avec une erreur de mémoire insuffisante. Si vous désactivez la pagination, vous devez accorder des privilèges Windows au compte de service. Pour obtenir des instructions, consultez [Configurer les comptes de service &#40;Analysis Services&#41;](../instances/configure-service-accounts-analysis-services.md).  
  
 **1** est la valeur par défaut. Cette propriété active la pagination sur le disque à l'aide du fichier de pagination du système d'exploitation (pagefile.sys).  
  
 Lorsque `VertiPaqPagingPolicy` est défini sur 1, le traitement est moins susceptible d’échouer en raison des contraintes de mémoire, car le serveur tente de paginer sur le disque à l’aide de la méthode que vous avez spécifié. La définition de la propriété `VertiPaqPagingPolicy` ne garantit pas que les erreurs de mémoire ne se produiront pas. Les erreurs de mémoire insuffisante peuvent toujours se produire dans les conditions suivantes :  
  
-   Il n'y a pas assez de mémoire pour tous les dictionnaires. Au cours du traitement, Analysis Services verrouille les dictionnaires pour chaque colonne dans la mémoire et l’ensemble de ces éléments ne peut pas être supérieure à la valeur spécifiée pour `VertiPaqMemoryLimit`.  
  
-   L'espace d'adressage virtuel est insuffisant pour le processus.  
  
 Pour résoudre les erreurs persistantes de mémoire insuffisante, vous pouvez reconcevoir le modèle pour réduire la quantité de données à traiter, ou bien ajouter plus de mémoire physique à l'ordinateur.  
  
 S'applique au mode serveur tabulaire uniquement.  
  
 `VertiPaqMemoryLimit`  
 Si la pagination sur le disque est autorisée, cette propriété indique le niveau de la consommation de mémoire (en pourcentage de la mémoire totale) auquel la pagination démarre. La valeur par défaut est 60. Si la consommation de mémoire est inférieure à 60 %, le serveur ne paginera pas sur le disque.  
  
 Cette propriété varie selon le `VertiPaqPagingPolicyProperty`, qui doit être défini sur 1 pour autoriser la pagination se produise.  
  
 S'applique au mode serveur tabulaire uniquement.  
  
 `HighMemoryPrice`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MemoryHeapType`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 S'applique au mode serveur multidimensionnel uniquement.  
  
 `HeapTypeForObjects`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 S'applique au mode serveur multidimensionnel uniquement.  
  
 `DefaultPagesCountToReuse`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `HandleIA64AlignmentFaults`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MidMemoryPrice`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MinimumAllocatedMemory`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `PreAllocate`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `SessionMemoryLimit`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `WaitCountIfHighMemory`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les propriétés du serveur dans Analysis Services](server-properties-in-analysis-services.md)   
 [Déterminer le mode serveur d’une instance Analysis Services](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
