---
title: Propriétés du serveur (page Mémoire) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.serverproperties.memory.f1
ms.assetid: 46a77d4e-ab92-49d3-a14b-423462e50715
caps.latest.revision: 43
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: a2468e4cfdbbb9a123ac552c301929b9040176d8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045020"
---
# <a name="server-properties-memory-page"></a>Propriétés du serveur (page Mémoire)
  Cette page vous permet d'afficher et de modifier les options de mémoire de votre serveur. Lorsque **Mémoire minimale du serveur (en Mo)** a la valeur 0 et que **Mémoire maximale du serveur** a la valeur 2 147 483 647 Mo, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut bénéficier d'un volume optimal de mémoire à tout moment, selon la quantité de mémoire que le système d'exploitation et les autres applications utilisent simultanément. La mémoire est allouée au fur et à mesure des modifications de la charge de l'ordinateur et de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Vous pouvez également limiter l'allocation de cette mémoire dynamique aux valeurs minimale et maximale spécifiées ci-dessous.  
  
## <a name="options"></a>Options  
 **Mémoire minimale du serveur (en Mo)**  
 Spécifie que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit démarrer avec au moins la quantité minimale de mémoire allouée et ne doit pas libérer de mémoire en dessous de cette valeur. Spécifiez cette valeur en fonction de la taille et de l'activité de votre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Spécifiez toujours une valeur raisonnable pour cette option, afin de garantir que le système d'exploitation ne demande pas trop de mémoire à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ce qui affecterait les performances de Windows.  
  
 **Mémoire maximale du serveur (en Mo)**  
 Indique la quantité maximale de mémoire que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut allouer lors de son démarrage et de son exécution. Il est possible d'affecter une valeur spécifique à cette option de configuration si vous savez que plusieurs applications fonctionnent en même temps que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et que vous voulez garantir que ces applications disposent d'une mémoire suffisante pour s'exécuter. Si ces applications, telles que des serveurs Web ou de messagerie, n'exigent de mémoire que ponctuellement, n'intervenez pas sur l'option, car [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se chargera de libérer de la mémoire en fonction de leurs besoins. Cependant, les applications utilisent généralement toute la mémoire disponible au moment du démarrage et n'en demandent pas plus même en cas de besoin. Si une application qui se comporte de cette façon s'exécute sur le même ordinateur et en même temps que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], affectez à l'option une valeur qui garantit que la mémoire requise par l'application n'est pas allouée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les quantités minimales de mémoire que vous pouvez spécifier pour **max server memory** sont de 64 mégaoctets (Mo) pour les systèmes 32 bits et de 128 Mo pour les systèmes 64 bits.  
  
 **Mémoire de création de l'index (en Ko, 0 = mémoire dynamique)**  
 Spécifie la quantité de mémoire (en Ko) utilisée pendant les tris de création d'index. La valeur par défaut de zéro permet d'activer l'allocation dynamique et doit fonctionner dans la plupart des cas sans réglage supplémentaire ; toutefois, l'utilisateur peut entrer une valeur différente, comprise entre 704 et 2 147 483 647.  
  
> [!NOTE]  
>  Les valeurs comprises entre 1 et 703 ne sont pas autorisées. Si une valeur incluse dans cette plage est entrée, cette valeur est remplacée par la valeur 704.  
  
 **Mémoire minimale par requête (en Ko)**  
 Spécifie la quantité de mémoire (en Ko) à allouer pour l'exécution d'une requête. L'utilisateur peut spécifier une valeur comprise entre 512 et 2 147 483 647 Ko. La valeur par défaut est 1 024 Ko.  
  
 **Valeurs configurées**  
 Affiche les valeurs configurées pour les options de ce volet. Si vous modifiez ces valeurs, cliquez sur **Valeurs en cours d’exécution** pour vérifier si les modifications ont été prises en compte. Si ce n'est pas le cas, l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être d'abord redémarrée.  
  
 **Valeurs en cours d’exécution**  
 Affiche les valeurs en cours d'exécution pour les options de ce volet. Ces valeurs sont en lecture seule.  
  
## <a name="see-also"></a>Voir aussi  
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [server memory (options de configuration de serveur)](server-memory-server-configuration-options.md)  
  
  