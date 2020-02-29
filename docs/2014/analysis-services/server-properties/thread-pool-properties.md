---
title: Propriétés du pool de threads | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- PriorityRatio property
- threads [Analysis Services]
- MinThreads property
- NumThreads property
- MaxThreads property
- Concurrency property
ms.assetid: e2697bb6-6d3f-4621-b9fd-575ac39c2185
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3d2d2e9caae1a9837b91679033be1eafc763f266
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78175608"
---
# <a name="thread-pool-properties"></a>Propriétés du pool de threads
  
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise le multithreading pour de nombreuses opérations, afin d’optimiser les performances globales du serveur en exécutant plusieurs travaux en parallèle. Pour gérer les threads plus efficacement, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise des pools pour préallouer les threads et faciliter leur disponibilité pour le travail suivant.

 Chaque d'instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] possède son propre ensemble de pools de threads. Il existe des différences significatives dans la manière dont les instances tabulaires et multidimensionnelles utilisent les pools de threads. La différence la plus importante est que seules les solutions multidimensionnelles `IOProcess` utilisent le pool de threads. Par conséquent, la propriété `PerNumaNode` décrite dans cette rubrique n'est pas significative pour les instances tabulaires.

 Cette rubrique contient les sections suivantes :

-   [Gestion des threads dans Analysis Services](#bkmk_threadarch)

-   [Référence de propriété du pool de threads](#bkmk_propref)

-   [Définir GroupAffinity sur des threads affinité sur des processeurs dans un groupe de processeurs](#bkmk_groupaffinity)

-   [Définir PerNumaNode sur des threads d’e/s affinité sur des processeurs dans un nœud NUMA](#bkmk_pernumanode)

-   [Déterminer les paramètres actuels du pool de threads](#bkmk_currentsettings)

-   [Propriétés dépendantes ou connexes](#bkmk_related)

-   [À propos de MSMDSRV. INI](#bkmk_msmdrsrvini)

> [!NOTE]
>  Le déploiement tabulaire sur les systèmes NUMA n'est pas abordé dans cette rubrique. Bien que les solutions tabulaires puissent être correctement déployées sur les systèmes NUMA, les caractéristiques des performances de la technologie de base de données en mémoire utilisée par les modèles tabulaires peuvent offrir des avantages limités sur les architectures fortement montées en charge. Pour plus d’informations, consultez [Étude de cas Analysis Services : utilisation des modèles tabulaires dans les solutions commerciales à grande échelle](https://msdn.microsoft.com/library/dn751533.aspx) et [Besoins matériels d’une solution tabulaire](https://go.microsoft.com/fwlink/?LinkId=330359).

##  <a name="bkmk_threadarch"></a>Gestion des threads dans Analysis Services
 
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise le multithreading pour tirer profit des ressources processeur disponibles en augmentant le nombre de tâches exécutées en parallèle. Le moteur de stockage est multithread. Les travaux multithread qui sont exécutés dans le moteur de stockage comprennent le traitement d'objets en parallèle ou la gestion de requêtes discrètes envoyées au moteur de stockage, ou encore le retour des valeurs de données demandées par une requête. Le moteur de formule, en raison de la nature en série des calculs qu'il effectue, est monothread. Chaque requête s'exécute principalement sur un seul thread et interroge, et souvent attend, les données retournées par le moteur de stockage. L'exécution des threads de requête est plus longue, et les threads sont libérés uniquement lorsque la totalité de la requête est terminée.

 Par défaut, sur les versions [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et les versions ultérieures, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise tous les processeurs logiques disponibles. Le nombre de processeurs peut atteindre 640 sur les systèmes exécutant des versions supérieures de Windows et SQL Server. Au démarrage, le processus msmdsrv.exe est attribué à un groupe de processeurs spécifique, mais les threads peuvent être planifiés ultérieurement sur n'importe quel processeur logique, dans tout groupe de processeurs.

 L'utilisation d'un grand nombre de processeurs peut avoir comme effet secondaire une dégradation des performances lorsque les charges de requête et de traitement sont distribuées sur un grand nombre de processeurs et la contention des structures de données partagées augmente. Cela peut se produire en particulier sur les systèmes haut de gamme qui utilisent l'architecture NUMA, mais également sur les systèmes non-NUMA exécutant plusieurs applications consommant de grandes quantités de données sur le même matériel.

 Pour réduire ce problème, vous pouvez définir une affinité entre les types d'opérations [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et un ensemble spécifique de processeurs logiques. La propriété `GroupAffinity` vous permet de créer des masques d'affinité personnalisés qui spécifient quelle ressource système utiliser pour chacun des types de pools de threads gérés par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].

 Une affinité personnalisée peut être définie sur l'un des cinq pools de threads utilisés pour différentes charges de travail [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] :

-   L' **analyse \ Short** est un pool d’analyse pour les requêtes courtes. Les requêtes qui tiennent dans un seul message réseau sont considérées comme courtes.

-   **Analyse \ long** est un pool d’analyse pour toutes les autres requêtes qui ne tiennent pas dans un seul message réseau.

    > [!NOTE]
    >  Un thread de l'un des pools d'analyse peut être utilisé pour exécuter une requête. Les requêtes qui s'exécutent rapidement, comme les requêtes de découverte ou d'annulation rapides, sont parfois exécutées immédiatement et ne sont pas mises en file d'attente dans le pool de threads de requêtes.

-   `Query`est le pool de threads qui exécute toutes les requêtes qui ne sont pas gérées par le pool de threads d’analyse. Les threads dans ce pool de threads exécuteront tous les types d'opérations, notamment les découvertes et les commandes MDX, DAX, DMX et DDL.

-   `IOProcess`est utilisé pour les travaux d’e/s associés aux requêtes du moteur de stockage dans le moteur multidimensionnel. Le travail exécuté par ces threads n'a normalement pas de dépendances sur d'autres threads. Ces threads analysent généralement un seul segment d'une partition et filtrent et agrègent les données du segment. `IOProcess`les threads sont particulièrement sensibles aux configurations matérielles NUMA. Par conséquent, ce pool de threads `PerNumaNode` dispose de la propriété de configuration qui peut être utilisée pour optimiser les performances si nécessaire.

-   `Process`est destiné aux travaux du moteur de stockage de plus longue durée, y compris les agrégations, les indexations et les opérations de validation. Le mode de stockage ROLAP utilise également des threads du pool de threads Processing.

> [!NOTE]
>  Bien que msmdsrv. ini comporte des paramètres de pool `VertiPaq` de threads dans la section `VertiPaq` \\ `ThreadPool` \\ `GroupAffinity` et `ThreadPool` \\ `CPUs` n’est volontairement pas documenté. En effet, ces propriétés sont actuellement inopérantes et sont réservés à une utilisation ultérieure.

 Pour traiter les demandes, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] peut dépasser la limite maximale de pool de threads, demandant des threads supplémentaires s'ils sont nécessaires pour exécuter le travail. Cependant, lorsqu'un thread termine d'exécuter sa tâche, si le nombre de threads actuel est supérieur à la limite maximale, le thread est simplement terminé, plutôt qu'être retourné au pool de threads.

> [!NOTE]
>  Le dépassement du nombre maximal de pools de threads est une protection appelée uniquement lorsque certaines conditions d'interblocage se produisent. Pour éviter la perte de contrôle de la création de threads au-delà du nombre maximal, les threads sont créés progressivement (après un délai court) après que le nombre maximal a été atteint. Le dépassement du nombre maximal de threads peut entraîner un ralentissement de l'exécution des tâches. Si les compteurs de performance indiquent que le nombre de threads dépasse régulièrement la taille maximale du pool de threads, il peut s'agir d'un indicateur de tailles de pool de threads trop petites pour le degré de concurrence actuellement demandé au système.

 Par défaut, la taille du pool de threads est déterminée par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]en fonction du nombre de cœurs. Vous pouvez observer les valeurs par défaut sélectionnées en consultant le fichier msmdsrv.log après le démarrage du serveur. Pour vous exercer au réglage des performances, vous pouvez choisir d'augmenter la taille du pool de threads et modifier d'autres propriétés, pour améliorer les performances des requêtes et des traitements.

##  <a name="bkmk_propref"></a>Référence de propriété du pool de threads
 Cette section décrit les propriétés de pool de threads qui se trouvent dans le fichier msmdsrv.ini de chaque instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Un sous-ensemble de ces propriétés apparaît également dans SQL Server Management Studio.

 Les propriétés sont répertoriées par ordre alphabétique.

|Nom|Type|Description|Default|Assistance|
|----------|----------|-----------------|-------------|--------------|
|`IOProcess` \ `Concurrency`|double|Valeur à virgule flottante double précision qui détermine l'algorithme pour définir une cible sur le nombre de threads pouvant être mis en file d'attente en même temps.|2.0|Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .<br /><br /> La concurrence est utilisée pour initialiser les pools de threads qui sont implémentés avec des ports de terminaison d'E/S dans Windows. Consultez [Ports de terminaison d’E/S](https://msdn.microsoft.com/library/windows/desktop/aa365198\(v=vs.85\).aspx) pour plus d’informations.<br /><br /> S'applique aux modèles multidimensionnels uniquement.|
|`IOProcess` \ `GroupAffinity`|string|Tableau de valeurs hexadécimales qui correspondent aux groupes de processeurs sur le système, utilisé pour définir l'affinité des threads dans le pool de threads IOProcess avec des processeurs logiques dans chaque groupe de processeurs.|Aucun|Vous pouvez utiliser cette propriété pour créer des affinités personnalisées. La propriété est vide par défaut.<br /><br /> Consultez [Définir GroupAffinity pour configurer l'affinité des threads à des processeurs dans un groupe de processeurs](#bkmk_groupaffinity) pour plus d'informations.<br /><br /> S'applique aux modèles multidimensionnels uniquement.|
|`IOProcess` \ `MaxThreads`|int|Nombre entier signé 32 bits qui spécifie le nombre maximal de threads à inclure dans le pool de threads.|0|0 indique que le serveur détermine les valeurs par défaut. Par défaut, le serveur définit cette valeur sur 64, ou 10 fois le nombre de processeurs logiques, la valeur la plus élevée étant applicable. Par exemple, sur un système 4 processeurs avec hyperthreading, la taille maximale du pool de threads est 80 threads.<br /><br /> Si vous attribuez à cette valeur une valeur négative, le serveur multiplie cette valeur par le nombre de processeurs logiques. Par exemple, si vous indiquez -10 sur un serveur qui possède 32 processeurs logiques, le maximum est 320 threads.<br /><br /> La valeur maximale dépend des processeurs disponibles en fonction des masques d'affinité personnalisés définis précédemment. Par exemple, si vous avez déjà défini l'affinité du pool de threads pour utiliser 8 processeurs sur 32, et si vous définissez maintenant MaxThreads sur -10, alors la limite supérieure du pool de threads sera égale à 10 fois 8, soit 80 threads.<br /><br /> Les valeurs réelles utilisées pour cette propriété de pool de threads sont écrites dans le fichier journal msmdsrv au démarrage du service.<br /><br /> Pour plus d'informations sur le réglage des paramètres de pool de threads, consultez [Guide des opérations d'Analysis Services](https://msdn.microsoft.com/library/hh226085.aspx).<br /><br /> S'applique aux modèles multidimensionnels uniquement.|
|`IOProcess` \ `MinThreads`|int|Nombre entier signé 32 bits qui spécifie le nombre minimal de threads à préallouer pour le pool de threads.|0|0 indique que le serveur détermine les valeurs par défaut. La valeur minimale par défaut est 1.<br /><br /> Si vous attribuez à cette valeur une valeur négative, le serveur multiplie cette valeur par le nombre de processeurs logiques.<br /><br /> Les valeurs réelles utilisées pour cette propriété de pool de threads sont écrites dans le fichier journal msmdsrv au démarrage du service.<br /><br /> Pour plus d'informations sur le réglage des paramètres de pool de threads, consultez [Guide des opérations d'Analysis Services](https://msdn.microsoft.com/library/hh226085.aspx).<br /><br /> S'applique aux modèles multidimensionnels uniquement.|
|`IOProcess` \ `PerNumaNode`|int|Nombre entier signé 32 bits qui détermine le nombre de pools de threads créés pour le processus msmdsrv.|-1|Les valeurs valides sont -1, 0, 1, 2<br /><br /> -1 = Le serveur sélectionne une stratégie de pool de threads d'E/S différente en fonction du nombre de nœuds NUMA. Sur des systèmes comportant moins de 4 nœuds NUMA, le comportement du serveur est identique à 0 (un pool de threads IOProcess est créé pour le système). Sur des systèmes comportant 4 nœuds ou plus, le comportement est identique à 1 (des pools de threads IOProcess sont créés sur chaque nœud).<br /><br /> 0 = Désactive par pools de threads de nœud NUMA de sorte qu'il n'y ait qu'un seul pool de threads IOProcess utilisé par le processus msmdsrv.exe.<br /><br /> 1 = Active un seul pool de threads IOProcess par nœud NUMA.<br /><br /> 2 = Un seul pool de threads IOProcess par processeur logique. Les threads dans chaque pool de threads sont associés au nœud NUMA du processeur logique, avec le processeur idéal défini sur le processeur logique.<br /><br /> Consultez [Définir PerNumaNode pour configurer l'affinité des threads d'E/S aux processeurs dans un nœud NUMA](#bkmk_pernumanode) pour plus d'informations.<br /><br /> S'applique aux modèles multidimensionnels uniquement.|
|`IOProcess` \ `PriorityRatio`|int|Nombre entier signé 32 bits pouvant être utilisé pour vous assurer que des threads avec une priorité plus faible sont parfois exécutés même lorsqu'une file d'attente de priorité plus élevée contient des éléments.|2|Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .<br /><br /> S'applique aux modèles multidimensionnels uniquement.|
|`IOProcess` \ `StackSizeKB`|int|Nombre entier signé 32 bits pouvant être utilisé pour ajuster l'allocation de mémoire lors de l'exécution du thread.|0|Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .<br /><br /> S'applique aux modèles multidimensionnels uniquement.|
|**Analyse**  \ `Long` \ `Concurrency`|double|Valeur à virgule flottante double précision qui détermine l'algorithme pour définir une cible sur le nombre de threads pouvant être mis en file d'attente en même temps.|2.0|Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .<br /><br /> La concurrence est utilisée pour initialiser les pools de threads qui sont implémentés avec des ports de terminaison d'E/S dans Windows. Consultez [Ports de terminaison d’E/S](https://msdn.microsoft.com/library/windows/desktop/aa365198\(v=vs.85\).aspx) pour plus d’informations.|
|**Analyse**  \ `Long` \ `GroupAffinity`|string|Tableau de valeurs hexadécimales qui correspondent aux groupes de processeurs sur le système, utilisé pour définir l'affinité des threads d'analyse avec des processeurs logiques dans chaque groupe de processeurs.|Aucun|Vous pouvez utiliser cette propriété pour créer des affinités personnalisées. La propriété est vide par défaut.<br /><br /> Consultez [Définir GroupAffinity pour configurer l'affinité des threads à des processeurs dans un groupe de processeurs](#bkmk_groupaffinity) pour plus d'informations.|
|**Analyse**  \ `Long` \ `NumThreads`|int|Propriété dont la valeur est un entier 32 bits signé qui définit le nombre de threads qu'il est possible de créer pour des commandes longues.|0|0 indique que ce serveur détermine les valeurs par défaut. Le comportement par défaut consiste à définir `NumThreads` à une valeur absolue de 4 ou 2 fois le nombre de processeurs logiques, la valeur la plus élevée étant applicable.<br /><br /> Si vous attribuez à cette valeur une valeur négative, le serveur multiplie cette valeur par le nombre de processeurs logiques. Par exemple, si vous indiquez -10 sur un serveur qui possède 32 processeurs logiques, le maximum est 320 threads.<br /><br /> La valeur maximale dépend des processeurs disponibles en fonction des masques d'affinité personnalisés définis précédemment. Par exemple, si vous avez déjà défini l'affinité du pool de threads pour utiliser 8 processeurs sur 32, et si vous définissez maintenant NumThreads sur -10, alors la limite supérieure du pool de threads sera égale à 10 fois 8, soit 80 threads.<br /><br /> Les valeurs réelles utilisées pour cette propriété de pool de threads sont écrites dans le fichier journal msmdsrv au démarrage du service.|
|**Analyse**  \ `Long` \ `PriorityRatio`|int|Nombre entier signé 32 bits pouvant être utilisé pour vous assurer que des threads avec une priorité plus faible sont parfois exécutés même lorsqu'une file d'attente de priorité plus élevée contient des éléments.|0|Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .|
|**Analyse**  \ `Long` \ `StackSizeKB`|int|Nombre entier signé 32 bits pouvant être utilisé pour ajuster l'allocation de mémoire lors de l'exécution du thread.|0|Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .|
|**Analyse**  \ `Short` \ `Concurrency`|double|Valeur à virgule flottante double précision qui détermine l'algorithme pour définir une cible sur le nombre de threads pouvant être mis en file d'attente en même temps.|2.0|Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .<br /><br /> La concurrence est utilisée pour initialiser les pools de threads qui sont implémentés avec des ports de terminaison d'E/S dans Windows. Consultez [Ports de terminaison d’E/S](https://msdn.microsoft.com/library/windows/desktop/aa365198\(v=vs.85\).aspx) pour plus d’informations.|
|**Analyse**  \ `Short` \ `GroupAffinity`|string|Tableau de valeurs hexadécimales qui correspondent aux groupes de processeurs sur le système, utilisé pour définir l'affinité des threads d'analyse avec des processeurs logiques dans chaque groupe de processeurs.|Aucun|Vous pouvez utiliser cette propriété pour créer des affinités personnalisées. La propriété est vide par défaut.<br /><br /> Consultez [Définir GroupAffinity pour configurer l'affinité des threads à des processeurs dans un groupe de processeurs](#bkmk_groupaffinity) pour plus d'informations.|
|**Analyse**  \ `Short` \ `NumThreads`|int|Propriété dont la valeur est un entier 32 bits signé qui définit le nombre de threads qu'il est possible de créer pour des commandes courtes.|0|0 indique que ce serveur détermine les valeurs par défaut. Le comportement par défaut consiste à définir `NumThreads` à une valeur absolue de 4 ou 2 fois le nombre de processeurs logiques, la valeur la plus élevée étant applicable.<br /><br /> Si vous attribuez à cette valeur une valeur négative, le serveur multiplie cette valeur par le nombre de processeurs logiques. Par exemple, si vous indiquez -10 sur un serveur qui possède 32 processeurs logiques, le maximum est 320 threads.<br /><br /> La valeur maximale dépend des processeurs disponibles en fonction des masques d'affinité personnalisés définis précédemment. Par exemple, si vous avez déjà défini l'affinité du pool de threads pour utiliser 8 processeurs sur 32, et si vous définissez maintenant NumThreads sur -10, alors la limite supérieure du pool de threads sera égale à 10 fois 8, soit 80 threads.<br /><br /> Les valeurs réelles utilisées pour cette propriété de pool de threads sont écrites dans le fichier journal msmdsrv au démarrage du service.|
|**Analyse**  \ `Short` \ `PriorityRatio`|int|Nombre entier signé 32 bits pouvant être utilisé pour vous assurer que des threads avec une priorité plus faible sont parfois exécutés même lorsqu'une file d'attente de priorité plus élevée contient des éléments.|0|Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .|
|**Analyse**  \ `Short` \ `StackSizeKB`|int|Nombre entier signé 32 bits pouvant être utilisé pour ajuster l'allocation de mémoire lors de l'exécution du thread.|64 * processeurs logiques|Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .|
|`Process` \ `Concurrency`|double|Valeur à virgule flottante double précision qui détermine l'algorithme pour définir une cible sur le nombre de threads pouvant être mis en file d'attente en même temps.|2.0|Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .<br /><br /> La concurrence est utilisée pour initialiser les pools de threads qui sont implémentés avec des ports de terminaison d'E/S dans Windows. Consultez [Ports de terminaison d’E/S](https://msdn.microsoft.com/library/windows/desktop/aa365198\(v=vs.85\).aspx) pour plus d’informations.|
|`Process` \ `GroupAffinity`|string|Tableau de valeurs hexadécimales qui correspondent aux groupes de processeurs sur le système, utilisé pour définir l'affinité des threads de traitement avec des processeurs logiques dans chaque groupe de processeurs.|Aucun|Vous pouvez utiliser cette propriété pour créer des affinités personnalisées. La propriété est vide par défaut.<br /><br /> Consultez [Définir GroupAffinity pour configurer l'affinité des threads à des processeurs dans un groupe de processeurs](#bkmk_groupaffinity) pour plus d'informations.|
|`Process` \ `MaxThreads`|int|Nombre entier signé 32 bits qui spécifie le nombre maximal de threads à inclure dans le pool de threads.|0|0 indique que le serveur détermine les valeurs par défaut. Par défaut, le serveur attribue à cette valeur une valeur absolue de 64, ou le nombre de processeurs logiques, la valeur la plus élevée étant applicable. Par exemple, sur un système 64 processeurs avec hyperthreading (soit, 128 processeurs logiques), la taille maximale du pool de threads est 128 threads.<br /><br /> Si vous attribuez à cette valeur une valeur négative, le serveur multiplie cette valeur par le nombre de processeurs logiques. Par exemple, si vous indiquez -10 sur un serveur qui possède 32 processeurs logiques, le maximum est 320 threads.<br /><br /> La valeur maximale dépend des processeurs disponibles en fonction des masques d'affinité personnalisés définis précédemment. Par exemple, si vous avez déjà défini l'affinité du pool de threads pour utiliser 8 processeurs sur 32, et si vous définissez maintenant MaxThreads sur -10, alors la limite supérieure du pool de threads sera égale à 10 fois 8, soit 80 threads.<br /><br /> Les valeurs réelles utilisées pour cette propriété de pool de threads sont écrites dans le fichier journal msmdsrv au démarrage du service.<br /><br /> Pour plus d'informations sur le réglage des paramètres de pool de threads, consultez [Guide des opérations d'Analysis Services](https://msdn.microsoft.com/library/hh226085.aspx).|
|`Process` \ `MinThreads`|int|Nombre entier signé 32 bits qui spécifie le nombre minimal de threads à préallouer pour le pool de threads.|0|0 indique que le serveur détermine les valeurs par défaut. La valeur minimale par défaut est 1.<br /><br /> Si vous attribuez à cette valeur une valeur négative, le serveur multiplie cette valeur par le nombre de processeurs logiques.<br /><br /> Les valeurs réelles utilisées pour cette propriété de pool de threads sont écrites dans le fichier journal msmdsrv au démarrage du service.<br /><br /> Pour plus d'informations sur le réglage des paramètres de pool de threads, consultez [Guide des opérations d'Analysis Services](https://msdn.microsoft.com/library/hh226085.aspx).|
|`Process` \ `PriorityRatio`|int|Nombre entier signé 32 bits pouvant être utilisé pour vous assurer que des threads avec une priorité plus faible sont parfois exécutés même lorsqu'une file d'attente de priorité plus élevée contient des éléments.|2|Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .|
|`Process` \ `StackSizeKB`|int|Nombre entier signé 32 bits pouvant être utilisé pour ajuster l'allocation de mémoire lors de l'exécution du thread.|0|Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .|
|`Query`  \ `Concurrency`|double|Valeur à virgule flottante double précision qui détermine l'algorithme pour définir une cible sur le nombre de threads pouvant être mis en file d'attente en même temps.|2.0|Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .<br /><br /> La concurrence est utilisée pour initialiser les pools de threads qui sont implémentés avec des ports de terminaison d'E/S dans Windows. Consultez [Ports de terminaison d’E/S](https://msdn.microsoft.com/library/windows/desktop/aa365198\(v=vs.85\).aspx) pour plus d’informations.|
|`Query` \ `GroupAffinity`|string|Tableau de valeurs hexadécimales qui correspondent aux groupes de processeurs sur le système, utilisé pour définir l'affinité des threads de traitement avec des processeurs logiques dans chaque groupe de processeurs.|Aucun|Vous pouvez utiliser cette propriété pour créer des affinités personnalisées. La propriété est vide par défaut.<br /><br /> Consultez [Définir GroupAffinity pour configurer l'affinité des threads à des processeurs dans un groupe de processeurs](#bkmk_groupaffinity) pour plus d'informations.|
|`Query`  \ `MaxThreads`|int|Nombre entier signé 32 bits qui spécifie le nombre maximal de threads à inclure dans le pool de threads.|0|0 indique que le serveur détermine les valeurs par défaut. Par défaut, le serveur attribue à cette valeur une valeur absolue de 10, ou 2 fois le nombre de processeurs logiques, la valeur la plus élevée étant applicable. Par exemple, sur un système 4 processeurs avec hyperthreading, le nombre maximal de threads est 16.<br /><br /> Si vous attribuez à cette valeur une valeur négative, le serveur multiplie cette valeur par le nombre de processeurs logiques. Par exemple, si vous indiquez -10 sur un serveur qui possède 32 processeurs logiques, le maximum est 320 threads.<br /><br /> La valeur maximale dépend des processeurs disponibles en fonction des masques d'affinité personnalisés définis précédemment. Par exemple, si vous avez déjà défini l'affinité du pool de threads pour utiliser 8 processeurs sur 32, et si vous définissez maintenant MaxThreads sur -10, alors la limite supérieure du pool de threads sera égale à 10 fois 8, soit 80 threads.<br /><br /> Les valeurs réelles utilisées pour cette propriété de pool de threads sont écrites dans le fichier journal msmdsrv au démarrage du service.<br /><br /> Pour plus d'informations sur le réglage des paramètres de pool de threads, consultez [Guide des opérations d'Analysis Services](https://msdn.microsoft.com/library/hh226085.aspx).|
|`Query` \ `MinThreads`|int|Nombre entier signé 32 bits qui spécifie le nombre minimal de threads à préallouer pour le pool de threads.|0|0 indique que le serveur détermine les valeurs par défaut. La valeur minimale par défaut est 1.<br /><br /> Si vous attribuez à cette valeur une valeur négative, le serveur multiplie cette valeur par le nombre de processeurs logiques.<br /><br /> Les valeurs réelles utilisées pour cette propriété de pool de threads sont écrites dans le fichier journal msmdsrv au démarrage du service.<br /><br /> Pour plus d'informations sur le réglage des paramètres de pool de threads, consultez [Guide des opérations d'Analysis Services](https://msdn.microsoft.com/library/hh226085.aspx).|
|`Query` \ `PriorityRatio`|int|Nombre entier signé 32 bits pouvant être utilisé pour vous assurer que des threads avec une priorité plus faible sont parfois exécutés même lorsqu'une file d'attente de priorité plus élevée contient des éléments.|2|Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .|
|`Query`  \ `StackSizeKB`|int|Nombre entier signé 32 bits pouvant être utilisé pour ajuster l'allocation de mémoire lors de l'exécution du thread.|0|Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .|

##  <a name="bkmk_groupaffinity"></a>Définir GroupAffinity sur des threads affinité sur des processeurs dans un groupe de processeurs
 
  `GroupAffinity` est destiné à un paramétrage avancé. Vous pouvez utiliser la propriété `GroupAffinity` pour définir l'affinité entre les pools de threads [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et des processeurs spécifiques. Toutefois, pour la plupart des installations, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] offre de meilleures performances lorsqu'il peut utiliser tous les processeurs logiques disponibles. Par conséquent, l'affinité de groupe n'est pas spécifiée par défaut.

 Si les tests de performance indiquent qu'il faut optimiser l'UC, vous devriez envisager une approche de niveau supérieur, par exemple, en utilisant le gestionnaire de ressources de Windows Server pour définir l'affinité entre les processeurs logiques et un processus du serveur. Une telle approche sera plus simple à implémenter et gérer que celle consistant à définir des affinités personnalisées pour chaque pool de threads.

 Si cette approche ne suffit pas, vous pouvez atteindre une meilleure précision en définissant des affinités personnalisées pour les pools de threads. La personnalisation des paramètres d'affinité est davantage recommandée dans les systèmes à plusieurs noyaux (NUMA ou non-NUMA) qui connaissent une dégradation des performances en raison de pools de threads étendus sur une plage de processeurs trop vaste. Bien que vous puissiez définir `GroupAffinity` sur les systèmes comportant moins de 64 processeurs logiques, l'avantage est négligeable et peut même dégrader les performances.

> [!NOTE]
>  
  `GroupAffinity` est contraint par les éditions qui limitent le nombre de noyaux utilisés par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Au démarrage, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise les informations d'édition et les propriétés `GroupAffinity` pour calculer des masques d'affinité pour chacun des 5 pools de threads gérés par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. L'édition standard peut utiliser jusqu'à 16 noyaux. Si vous installez l'édition actuelle d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sur un grand système à plusieurs noyaux qui contient plus de 16 noyaux, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilisera uniquement 16 d'entre eux. Si vous mettez à niveau une instance Enterprise d'une version antérieure, vous êtes limité à 20 noyaux. Pour plus d'informations sur les éditions et les licences, consultez [Vue d'ensemble des licences SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=246061).

### <a name="syntax"></a>Syntaxe
 La valeur est hexadécimale pour chaque groupe de processeurs, et représente les processeurs logiques que [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tente d'utiliser d'abord lorsqu'il alloue des threads pour un pool de threads donné.

 **Masque de binaire pour les processeurs logiques**

 Vous pouvez avoir jusqu'à 64 processeurs logiques dans un seul groupe du processeurs. Le masque de bits est 1 (ou 0) pour chaque processeur logique dans le groupe utilisé (ou non) par un pool de threads. Une fois que vous avez calculé le masque de masque, vous calculez ensuite la valeur `GroupAffinity`hexadécimale comme valeur pour.

 **Plusieurs groupes de processeurs**

 Les groupes de processeurs sont déterminés au démarrage du système. `GroupAffinity`accepte des valeurs hexadécimales pour chaque groupe de processeurs dans une liste séparée par des virgules. Si plusieurs groupes de processeurs sont utilisés (jusqu'à 10 dans les systèmes haut de gamme), vous pouvez ignorer certains groupes en spécifiant 0x0. Par exemple, sur un système avec quatre groupes de processeurs (0, 1, 2, 3), vous pouvez exclure les groupes 0 et 2 en entrant 0x0 pour les première et troisième valeurs.

 `<GroupAffinity>0x0, 0xFF, 0x0, 0xFF</GroupAffinity>`

### <a name="steps-for-computing-the-processor-affinity-mask"></a>Étapes pour calculer le masque d'affinité du processeur
 Vous pouvez définir `GroupAffinity` dans msmdsrv. ini ou dans les pages de propriétés du serveur dans SQL Server Management Studio.

1.  **Déterminer le nombre de processeurs et de groupes de processeurs**

     Vous pouvez télécharger l' [Utilitaire Coreinfo depuis winsysinternals](https://technet.microsoft.com/sysinternals/cc835722.aspx).

     Exécutez **coreinfo** pour obtenir ces informations dans la section de mise en correspondance des processeurs logiques et des groupes. Une ligne distincte est générée pour chaque processeur logique.

2.  Numérotez les processeurs, de droite à gauche : `7654 3210`

     L'exemple affiche uniquement 8 processeurs (0 à 7), mais un groupe de processeurs peut avoir jusqu'à 64 processeurs logiques, et il peut exister jusqu'à 10 groupes de processeurs dans un serveur Windows de niveau entreprise.

3.  **Calculer le masque de réutilisation pour les groupes de processeurs que vous souhaitez utiliser**

     `7654 3210`

     Remplacez le nombre par un 0 ou 1, selon si vous souhaitez inclure ou exclure le processeur logique. Sur un système avec huit processeurs, votre calcul sera semblable à celui-ci si vous souhaitez utiliser les processeurs 7, 6, 5, 4, et 1 pour Analysis Services :

     `1111 0010`

4.  **Convertir le nombre binaire en valeur hexadécimale**

     Avec une calculatrice ou un outil de conversion, convertissez le nombre binaire en son équivalent hexadécimal. Dans notre exemple, `1111 0010` devient `0xF2`.

5.  **Entrez la valeur hexadécimale dans la propriété GroupAffinity**

     Dans msmdsrv. ini ou dans la page de propriétés du serveur de Management Studio `GroupAffinity` , définissez sur la valeur calculée à l’étape 4.

> [!IMPORTANT]
>  Le `GroupAffinity` paramètre est une tâche manuelle qui comprend plusieurs étapes. Lorsque vous `GroupAffinity`Calculez, vérifiez attentivement vos calculs. 
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] retourne une erreur si le masque entier n'est pas valide, mais si une combinaison de valeurs valides et non valides est présente, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ignore la propriété. Par exemple, si le masque de bits contient des valeurs supplémentaires, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ignore le paramètre et utilise tous les processeurs du système. Aucune erreur ni aucun avertissement ne vous informe lorsque cette action se produit, mais vous pouvez consulter le fichier msmdsrv.log pour déterminer comment les affinités sont vraiment définies.

##  <a name="bkmk_pernumanode"></a>Définir PerNumaNode sur des threads d’e/s affinité sur des processeurs dans un nœud NUMA
 Pour les instances multidimensionnelles Analysis Services, vous pouvez `PerNumaNode` définir sur `IOProcess` le pool de threads pour optimiser davantage la planification et l’exécution des threads. Tandis que `GroupAffinity` identifie l’ensemble de processeurs logiques à utiliser pour un `PerNumaNode` pool de threads donné, en spécifiant s’il faut créer plusieurs pools de threads, affinité davantage à un sous-ensemble des processeurs logiques autorisés.

> [!NOTE]
>  Sous Windows Server 2012, utilisez le Gestionnaire des tâches pour afficher le nombre de nœuds NUMA sur l'ordinateur. Dans le Gestionnaire des tâches, sous l’onglet Performances, sélectionnez **UC** , puis cliquez avec le bouton droit sur la zone graphique pour afficher les nœuds NUMA. Vous pouvez aussi [télécharger](https://technet.microsoft.com/sysinternals/cc835722.aspx) l'utilitaire Coreinfo depuis Windows Sysinternals et exécuter `coreinfo -n` pour retourner les nœuds NUMA et les processeurs logiques dans chaque nœud.

 Les valeurs valides pour `PerNumaNode` sont-1, 0, 1, 2, comme décrit dans la section Référence de propriété du pool de [Threads](#bkmk_propref) dans cette rubrique.

### <a name="default-recommended"></a>Par défaut (recommandé)
 Sur des systèmes comportant des nœuds NUMA, nous recommandons d’utiliser le paramètre par défaut PerNumaNode=-1, pour permettre à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] d’ajuster le nombre de pools de threads et l’affinité des threads en fonction du nombre de nœuds. Si le système comporte moins de 4 nœuds [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , implémente les comportements décrits par `PerNumaNode`= 0, tandis que `PerNumaNode`= 1 est utilisé sur les systèmes comportant 4 nœuds ou plus.

### <a name="choosing-a-value"></a>Choix d'une valeur
 Vous pouvez également remplacer la valeur par défaut et utiliser une autre valeur valide.

 **Définition de PerNumaNode = 0**

 Les nœuds NUMA sont ignorés. Il n'y aura qu'un seul pool de threads IOProcess, et tous les threads dans le pool posséderont une affinité avec l'ensemble des processeurs logiques. Par défaut (où PerNumaNode=-1) ; il s'agit du paramètre opérationnel si l'ordinateur possède moins de 4 nœuds NUMA.

 ![Correspondance NUMA, du processeur et du pool de threads](../media/ssas-threadpool-numaex0.PNG "Correspondance NUMA, du processeur et du pool de threads")

 **Paramètre PerNumaNode = 1**

 Les pools de threads IOProcess sont créés pour chaque nœud NUMA. Des pools de threads distincts améliorent l'accès coordonné aux ressources locales, telles que le cache local sur un nœud NUMA.

 ![Correspondance NUMA, du processeur et du pool de threads](../media/ssas-threadpool-numaex1.PNG "Correspondance NUMA, du processeur et du pool de threads")

 **Définition de PerNumaNode = 2**

 Ce paramètre est destiné aux systèmes très haut de gamme qui exécutent des charges de travail [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] consommant beaucoup de ressources. Cette propriété définit l'affinité de pool de threads IOProcess à son niveau le plus granulaire, créant et configurant l'affinité des pools de threads distincts au niveau du processeur logique.

 Dans l’exemple suivant, sur un système comportant 4 nœuds NUMA et 32 processeurs logiques, l’affectation de la valeur `PerNumaNode` 2 a pour résultat 32 pools de threads IOProcess. Les threads dans les 8 premiers pools sont associés à tous les processeurs logiques dans le nœud NUMA 0, mais avec le processeur idéal défini sur 0, 1, 2, jusqu'à 7. Les 8 pools de threads suivants sont associés à tous les processeurs logiques dans le nœud NUMA 1, avec le processeur idéal défini sur 8, 9, 10, jusqu'à 15, et ainsi de suite.

 ![Correspondance NUMA, du processeur et du pool de threads](../media/ssas-threadpool-numaex2.PNG "Correspondance NUMA, du processeur et du pool de threads")

 À ce niveau d'affinité, le planificateur tente toujours d'utiliser le processeur logique idéal en premier, au sein du nœud NUMA préférentiel. Si le processeur logique est indisponible, le planificateur choisit un autre processeur dans le même nœud, ou dans le même du groupe de processeurs si aucun autre thread n'est disponible. Pour plus d’informations et des exemples, consultez [Paramètres de configuration d’Analysis Services 2012 (blog Wordpress)](https://go.microsoft.com/fwlink/?LinkId=330387).

###  <a name="bkmk_workdistrib"></a>Répartition du travail entre les threads IOProcess
 Lorsque vous envisagez de définir `PerNumaNode` la propriété, le `IOProcess` fait de savoir comment les threads sont utilisés peut vous aider à prendre une décision plus avisée.

 Rappelez `IOProcess` -vous que est utilisé pour les travaux d’e/s associés aux requêtes du moteur de stockage dans le moteur multidimensionnel.

 Lorsqu'un segment est analysé, le moteur identifie la partition à laquelle il appartient et tente de mettre le travail du segment en file d'attente dans le pool de threads utilisé par la partition. Généralement, tous les segments appartenant à une partition mettent en file d'attente leurs tâches sur le même pool de threads. Sur des systèmes NUMA, ce comportement est particulièrement avantageux car toutes les analyses d'une partition utiliseront la mémoire du cache de système de fichiers alloué localement à ce nœud NUMA.

 Les scénarios suivants suggèrent des réglages pouvant parfois améliorer les performances des requêtes sur les systèmes NUMA :

-   Pour les groupes de mesures sous-partitionnés (par exemple, comportant une seule partition), augmentez le nombre de partitions. Si vous utilisez une seule partition, le moteur met systématiquement en file d'attente les tâches sur un seul pool de threads (le pool de threads 0). L'ajout de davantage de partitions permet au moteur d'utiliser des pools de threads supplémentaires.

     Sinon, si vous ne pouvez pas créer de partitions supplémentaires, essayez `PerNumaNode`de définir = 0 pour augmenter le nombre de threads disponibles pour le pool de threads 0.

-   Pour les bases de données dans lesquelles les analyses de segment sont uniformément réparties sur plusieurs `PerNumaNode` partitions, le paramétrage sur 1 ou 2 peut améliorer les performances des requêtes `IOProcess` car cela augmente le nombre total de pools de threads utilisés par le système.

-   Pour les solutions qui ont plusieurs partitions, mais qu’une seule est fortement analysée, essayez `PerNumaNode`de définir = 0 pour voir si cela améliore les performances.

 Bien que les analyses de partition et de dimension `IOProcess` utilisent toutes deux le pool de threads, les analyses de dimension utilisent uniquement le pool de threads 0. Cela peut entraîner une charge légèrement inégale sur ce pool de threads, mais le déséquilibre devrait être temporaire, car les analyses de dimension ont tendance à être très rapides et peu fréquentes.

> [!NOTE]
>  Lorsque vous modifiez une propriété du serveur, souvenez-vous que l'option de configuration s'applique à toutes les bases de données qui s'exécutent sur l'instance actuelle. Sélectionnez les paramètres les plus avantageux pour les bases de données les plus importantes, ou pour le plus grand nombre de bases de données. Vous ne pouvez pas définir l'affinité du processeur au niveau de la base de données, ni l'affinité entre des partitions et des processeurs spécifiques.

 Pour plus d'informations sur l'architecture des travaux, consultez la section 2.2 dans [Guide des performances SQL Server 2008 Analysis Services](https://www.microsoft.com/download/details.aspx?id=17303).

##  <a name="bkmk_related"></a>Propriétés dépendantes ou connexes
 Comme expliqué dans la section 2,4 du [Guide des opérations Analysis Services](https://msdn.microsoft.com/library/hh226085.aspx), si vous augmentez le pool de threads de traitement, vous `CoordinatorExecutionMode` devez vous assurer que les paramètres `CoordinatorQueryMaxThreads` , ainsi que les paramètres, ont des valeurs qui vous permettent d’utiliser pleinement l’augmentation de la taille du pool de threads.

 Analysis Services utilise un thread de coordination afin de collecter les données nécessaires pour effectuer une demande de traitement ou de requête. Le coordinateur met d'abord en file d'attente un travail pour chaque partition concernée. Ensuite, chacun de ces travaux continue à mettre en file d'attente plus de travaux, en fonction du nombre total de segments qui doivent être analysés dans la partition.

 La valeur par défaut de `CoordinatorExecutionMode` est -4, soit une limite de 4 travaux pouvant être exécutés en parallèle par processeur, ce qui limite le nombre total de travaux du coordinateur pouvant être exécutés en parallèle par une requête de sous-cube dans le moteur de stockage.

 La valeur par défaut pour `CoordinatorQueryMaxThreads` est 16, ce qui limite le nombre de travaux de segment qui peuvent être exécutés en parallèle pour chaque partition.

##  <a name="bkmk_currentsettings"></a>Déterminer les paramètres actuels du pool de threads
 À chaque démarrage du service, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] génère les paramètres de pool de threads actuels dans le fichier msmdsrv.log, y compris le nombre minimal et maximal de threads, le masque d'affinité du processeur, et la concurrence.

 L'exemple suivant est un extrait du fichier journal, montrant les paramètres par défaut du pool de threads Query (MinThread=0, MaxThread=0, Concurrency=2), sur un système 4 processeurs avec hyperthreading. Le masque d'affinité est 0xFF, indiquant 8 processeurs logiques. Notez que des zéros sont ajoutés au début du masque. Vous pouvez ignorer les zéros de début.

 `"10/28/2013 9:20:52 AM) Message: The Query thread pool now has 1 minimum threads, 16 maximum threads, and a concurrency of 16.  Its thread pool affinity mask is 0x00000000000000ff. (Source: \\?\C:\Program Files\Microsoft SQL Server\MSAS11.MSSQLSERVER\OLAP\Log\msmdsrv.log, Type: 1, Category: 289, Event ID: 0x4121000A)"`

 N'oubliez pas que l'algorithme permettant de définir **MinThread** et **MaxThread** intègre la configuration du système, notamment le nombre de processeurs. La publication de blog suivante donne des éclaircissements sur la façon de calculer les valeurs : [Paramètres de configuration d’Analysis Services 2012 (blog Wordpress)](https://go.microsoft.com/fwlink/?LinkId=330387). Notez que ces paramètres et comportements sont susceptibles d'être modifiés dans les versions à venir.

 La liste suivante répertorie des exemples d'autres paramètres de masque d'affinité, pour différentes combinaisons de processeurs :

-   L'affinité pour les processeurs 3-2-1-0 sur un système à 8 processeurs aboutit à ce masque de bits : 00001111, et à une valeur hexadécimale : 0xF

-   L'affinité pour les processeurs 7-6-5-4 sur un système à 8 processeurs aboutit à ce masque de bits : 11110000, et une valeur hexadécimale : 0xF0

-   L'affinité pour les processeurs 5-4-3-2 sur un système à 8 processeurs aboutit à ce masque de bits : 00111100, et une valeur hexadécimale : 0x3C

-   L'affinité pour les processeurs 7-6-1-0 sur un système à 8 processeurs aboutit à ce masque de bits : 11000011, et une valeur hexadécimale : 0xC3

 Rappelez-vous que sur les systèmes avec plusieurs groupes de processeurs, un masque d'affinité distinct est généré pour chaque groupe, dans une liste séparée par des virgules.

##  <a name="bkmk_msmdrsrvini"></a>À propos de MSMDSRV. INI
 Le fichier msmdsrv.ini contient les paramètres de configuration pour une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , affectant toutes les bases de données en cours d'exécution sur cette instance. Vous ne pouvez pas utiliser les propriétés de configuration du serveur pour optimiser les performances d'une seule base de données à l'exclusion de toutes les autres. Toutefois, vous pouvez installer plusieurs instances de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et configurer chaque instance pour utiliser les propriétés les plus avantageuses pour les bases de données qui partagent des caractéristiques ou des charges de travail similaires.

 Toutes les propriétés de configuration du serveur sont incluses dans le fichier msmdsrv.ini. Les sous-ensembles de propriétés les plus susceptibles d'être modifiés apparaissent également dans les outils d'administration, comme SSMS.

 Le contenu de msmdsrv.ini est identique pour les instances tabulaires et multidimensionnelles de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Cependant, certains paramètres s'appliquent seulement à un mode. Des différences de comportement en mode serveur sont signalées dans la documentation relative aux références de propriété.

> [!NOTE]
>  Pour obtenir des instructions sur la définition des propriétés, consultez [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).

## <a name="see-also"></a>Voir aussi
 [À propos des processus et des threads](/windows/desktop/ProcThread/about-processes-and-threads) [plusieurs](/windows/desktop/ProcThread/multiple-processors) processeurs, [groupes de processeurs](/windows/desktop/ProcThread/processor-groups) [Analysis Services les modifications du Pool de threads dans SQL Server 2012](https://blogs.msdn.com/b/psssql/archive/2012/01/31/analysis-services-thread-pool-changes-in-sql-server-2012.aspx) [Analysis Services 2012 paramètres de configuration (blog WordPress)](https://go.microsoft.com/fwlink/?LinkId=330387) [qui prennent en charge des systèmes dotés de plus de 64 processeurs](https://msdn.microsoft.com/library/windows/hardware/gg463349.aspx) [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539)


