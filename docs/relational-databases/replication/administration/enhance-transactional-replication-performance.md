---
title: Améliorer les performances de la réplication transactionnelle | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publications [SQL Server replication], design and performance
- performance [SQL Server replication], transactional replication
- designing databases [SQL Server], replication performance
- performance [SQL Server replication], snapshot replication
- snapshot replication [SQL Server], performance
- subscriptions [SQL Server replication], performance considerations
- agents [SQL Server replication], performance
- Distribution Agent, performance
- transactional replication, performance
- Log Reader Agent, performance
ms.assetid: 67084a67-43ff-4065-987a-3b16d1841565
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 8ed18a3ea7ce4804146d448765d9f18e8b2a7f73
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76288176"
---
# <a name="enhance-transactional-replication-performance"></a>Améliorer les performances de la réplication transactionnelle
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Après avoir tenu compte des conseils de performances générales décrites dans [Amélioration des performances générales de la réplication](../../../relational-databases/replication/administration/enhance-general-replication-performance.md), envisagez ces domaines supplémentaires spécifiques à la réplication transactionnelle.  
  
## <a name="database-design"></a>Création de bases de données  
  
-   Réduisez la taille de transaction dans la conception de votre application.  
  
     Par défaut, la réplication transactionnelle propage les modifications en fonction des limites des transactions. Si les transactions sont plus petites, il est moins probable que l’Agent de distribution renvoie une transaction à cause de problèmes réseau. S'il est demandé à l'Agent de renvoyer une transaction, la quantité de données envoyée est moins importante. 

  
## <a name="distributor-configuration"></a>Configuration du serveur de distribution  
  
-   Configurez le serveur de distribution sur un serveur dédié.  
  
     Vous pouvez réduire la charge de traitement sur le serveur de publication en configurant un serveur de distribution distant. Pour plus d'informations, voir [Configure Distribution](../../../relational-databases/replication/configure-distribution.md).  
  
-   Dimensionnez correctement la base de données de distribution.  
  
     Testez la réplication avec une charge normale pour votre système afin de déterminer l'espace nécessaire au stockage des commandes. Assurez-vous que la base de données est suffisamment volumineuse pour stocker les commandes sans avoir fréquemment recours à l'extension automatique. Pour plus d’informations sur la modification de la taille d’une base de données, consultez [ALTER DATABASE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-database-transact-sql.md).  
  
## <a name="publication-design"></a>Conception de la publication  
  
-   Répliquez l'exécution d'une procédure stockée lors de mises à jour par lot de tables publiées.  
  
     Si des mises à jour par lots concernent parfois de nombreuses lignes sur l'abonné, vous devez envisager la mise à jour de la table publiée à l'aide d'une procédure stockée puis publier l'exécution de la procédure stockée. Au lieu d'envoyer une mise à jour ou une suppression pour chaque ligne affectée, l'Agent de distribution exécute la même procédure sur l'Abonné à partir des mêmes valeurs de paramètres. Pour plus d’informations, consultez [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
-   Répartissez les articles à travers plusieurs publications.  
  
     Si vous ne pouvez pas utiliser le [paramètre **-SubscriptionStreams**](#subscriptionstreams), envisagez la possibilité de créer plusieurs publications. La répartition d'articles sur ces publications permet à la réplication d'appliquer en parallèle les modifications sur les abonnés.  
  
## <a name="subscription-considerations"></a>Considérations sur les abonnements  
  
-   Utilisez les agents indépendants plutôt que les agents partagés si vous avez plusieurs publications sur le même serveur de publication (valeur par défaut pour l'Assistant Nouvelle publication).  
  
-   Exécutez les agents en continu et non par planifications fréquentes.  
  
     Le fait de configurer les agents afin qu'ils s'exécutent en mode continu au lieu de planifier de fréquentes exécutions (par exemple, toutes les minutes) permet d'améliorer les performances de la réplication, car l'Agent n'a pas besoin de démarrer et de s'arrêter. Lorsque vous configurez l'Agent de distribution pour qu'il s'exécute en mode continu, les modifications sont diffusées avec une faible latence aux autres serveurs de la topologie qui sont connectés. Pour plus d'informations, consultez les pages suivantes :  
  
    -   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] : [Spécifier des planifications de synchronisation](../../../relational-databases/replication/specify-synchronization-schedules.md)  
  
## <a name="distribution-agent-and-log-reader-agent-parameters"></a>Paramètres de l'Agent de distribution et de l'Agent de lecture du journal  
Les paramètres de profil de l’Agent sont souvent ajustés de manière à augmenter le débit de l’Agent de lecture du journal et de l’Agent de Distribution avec des systèmes OLTP à fort trafic. 

Des tests ont été effectués afin de déterminer les meilleures valeurs pour améliorer les performances de l’Agent de lecture du journal et de l’Agent de Distribution. Ils ont permis de conclure que la charge de travail était un facteur déterminant pour le choix des valeurs dans chaque cas ; il n’existe pas de valeur unique d’ajustement qui améliore les performances dans toutes les situations. 

Conclusions : 
- Pour un *Agent de lecture du journal* ayant comme charges de travail de petites transactions (moins de 500 commandes), une valeur **ReadBatchSize** élevée peut avoir un effet positif sur le débit. En revanche, dans le cas des charges de travail à gros volumes de transactions, modifier cette valeur n’améliore pas les performances. 
    - Lorsqu’il y a plusieurs Agents de lecture du journal et plusieurs Agents de distribution en cours d’exécution en parallèle sur le même serveur, une valeur **ReadBatchSize** élevée provoque une contention sur la base de données de distribution. 
- Pour *l’Agent de distribution* :
    - L’augmentation de **CommitBatchSize** est susceptible d’améliorer le débit. L’inconvénient est que, en cas de défaillance, l’Agent de distribution doit se restaurer et recommencer à zéro pour réappliquer un grand nombre de transactions. 
    - L’augmentation de la valeur **SubscriptionStreams** est positive pour le débit global de l’Agent de distribution, étant donné que plusieurs connexions à l’abonné appliquent en parallèle des modifications par lots. Toutefois, en fonction du nombre de processeurs et d’autres conditions liées aux métadonnées (par exemple, la clé primaire, les clés étrangères, les contraintes uniques et les index), une valeur SubscriptionStreams élevée risquerait en fait d’avoir un effet négatif. Par ailleurs, si l’exécution ou la validation d’un flux échoue, l’Agent de distribution se remet à utiliser un seul flux pour retenter d’exécuter les lots ayant échoué.


Pour plus d’informations sur ces tests, consultez le blog [Optimiser les paramètres de profil de l’agent de réplication pour obtenir de meilleures performances](https://blogs.msdn.microsoft.com/sql_server_team/optimizing-replication-agent-profile-parameters-for-better-performance/).


### <a name="log-reader-agent"></a>l'Agent de lecture du journal ;

#### <a name="readbatchsize"></a>ReadBatchSize
- Augmentez la valeur du paramètre **-ReadBatchSize** pour l’Agent de lecture du journal.  
  
L'Agent de lecture du journal et l'Agent de distribution prennent en charge des tailles de traitements pour les opérations de lecture et de validation des transactions. Par défaut, la taille de traitement est de 500 transactions. Dans ce cas, l'Agent de lecture du journal ne lit dans le journal que le nombre de transactions indiqué, que celles-ci soient marquées ou non pour réplication. Quand de nombreuses transactions sont écrites dans une base de données de publication, mais que seules quelques-unes sont marquées pour réplication, il est recommandé d’utiliser le paramètre **-ReadBatchSize** pour augmenter la taille des lots de lecture de l’Agent de lecture du journal. Ce paramètre ne s'applique pas aux serveurs de publication Oracle.  

   - Les charges de travail des petites transactions (moins de 500 commandes) constatent une augmentation du nombre de commandes traitées par seconde lorsque **ReadBatchSize** est augmenté jusqu’à 5 000. 
   - Dans le cas des grandes charges de travail (transactions entre 500 et 1 000 commandes), l’augmentation de **ReadBatchSize** offre peu d’amélioration des performances. Augmentation **ReadBatchSize** entraîne un plus grand nombre de transactions écrites dans la base de données de distribution dans un aller-retour. ce qui allonge la période pendant laquelle les transactions et les commandes sont visibles pour l’Agent de distribution et introduit une latence dans le processus de réplication.  

#### <a name="pollinginterval"></a>PollingInterval
- Réduisez la valeur du paramètre **-PollingInterval** pour l’Agent de lecture du journal.  
  
Le paramètre **-PollingInterval** indique la fréquence d’interrogation du journal des transactions d’une base de données publiée pour que les transactions soient répliquées. La valeur par défaut est 5 secondes. Si vous réduisez cette valeur, le journal est interrogé plus fréquemment, ce qui peut entraîner une latence plus faible pour la remise des transactions de la base de données de publication sur la base de données de distribution. Cependant, vous devriez équilibrer les besoins d'une latence plus faible en fonction de l'augmentation de la charge sur le serveur causée par une interrogation plus fréquente.   
  
#### <a name="maxcmdsintran"></a>MaxCmdsInTran
- Pour résoudre les goulots d’étranglement accidentels et occasionnels, utilisez le paramètre **–MaxCmdsInTran** pour l’Agent de lecture du journal.  
  
Le paramètre **–MaxCmdsInTran** indique le nombre maximal d’instructions groupées dans une transaction lorsque le Lecteur du journal enregistre des commandes sur la base de données de distribution. L'utilisation de ce paramètre permet à l'Agent de lecture du journal et à l'Agent de distribution de scinder les transactions importantes (constituées de plusieurs commandes) sur le serveur de publication en plusieurs transactions plus petites, lors de l'application des commandes sur l'Abonné. La spécification de ce paramètre permet de réduire les contentions sur le serveur de distribution et de réduire la latence entre le serveur de publication et l'Abonné. Du fait que la transaction d'origine est appliquée en plusieurs morceaux, l'Abonné peut accéder aux lignes d'une importante transaction logique du serveur de publication avant la fin de la transaction d'origine, ce qui rompt la stricte atomicité transactionnelle. La valeur par défaut est **0**, ce qui permet de conserver les limites de la transaction du serveur de publication. Ce paramètre ne s'applique pas aux serveurs de publication Oracle.  
  
   > [!WARNING]  
   >  **MaxCmdsInTran** n'a pas été conçu pour rester toujours activé. Il permet de contourner le problème lorsqu'un utilisateur a accidentellement exécuté un grand nombre d'opérations DML dans une seule transaction (provoquant un retard dans la distribution des commandes jusqu'à ce que la transaction entière soit dans la base de données de distribution, le maintien de verrous, etc.). Si vous vous retrouvez régulièrement dans cette situation, vérifiez vos applications et trouvez un moyen de réduire la taille des transactions.  
  
### <a name="distribution-agent"></a>Agent de distribution

#### <a name="subscriptionstreams"></a>SubscriptionStreams
- Augmentez le paramètre **–SubscriptionStreams** de l’Agent de distribution.  
  
Le paramètre **–SubscriptionStreams** permet d’améliorer sensiblement le débit de la réplication d’agrégation. Il autorise plusieurs connexions à l'Abonné pour appliquer des traitements de modifications en parallèle, tout en conservant la plupart des caractéristiques transactionnelles présentes lors de l'utilisation d'un thread unique. Si l'une des connexions ne réussit pas à s'exécuter ou n'est pas validée, toutes les connexions abandonneront le lot actuel, et l'Agent utilisera un flux unique pour une nouvelle tentative sur les lots ayant échoué. Avant que cette phase de nouvelle tentative ne se termine, il peut se produire des incohérences transactionnelles temporaires sur l'Abonné. Une fois que les lots ayant échoué sont validés avec succès, l'Abonné retrouve un état de cohérence transactionnelle.  
  
Il est possible d’indiquer une valeur pour le paramètre de cet agent à l’aide du `@subscriptionstreams` de [sp_addsubscription &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md).  

Pour plus d’informations sur l’implémentation des flux d’abonnements, voir [Parcourir le paramètre subscriptionStream de réplication SQL](https://blogs.msdn.microsoft.com/repltalk/2010/03/01/navigating-sql-replication-subscriptionstreams-setting).
  
### <a name="blocking-monitor-thread"></a>Thread de surveillance de blocage

L’Agent de distribution gère un thread de surveillance de blocage qui détecte les blocages entre les sessions. Si le thread de surveillance de blocage détecte des blocages entre les sessions, l’Agent de distribution bascule pour utiliser une session permettant de réappliquer le lot actuel des commandes qui n’a pas pu être appliqué avant.

Le thread de surveillance de blocage peut détecter des blocages entre les sessions de l’Agent de distribution. Toutefois, le thread de surveillance de blocage ne peut pas détecter les blocages dans les situations suivantes :
- L’une des sessions où le blocage se produit n’est pas une session de l’Agent de distribution.
- Un interblocage de session bloque les activités de l’Agent de distribution.

Dans ce cas, l’Agent de distribution coordonne toutes les sessions à valider ensemble dès que leurs commandes sont exécutées. Un interblocage entre les sessions se produit si les conditions suivantes sont réunies :

- Le blocage se produit entre les sessions de l’Agent de distribution et une session qui n’est pas une session de l’Agent de distribution.
- L’Agent de distribution attend que toutes les sessions terminent l’exécution de leurs commandes avant de coordonner toutes les sessions à valider ensemble.

Par exemple, vous configurez le paramètre *SubscriptionStreams* avec la valeur 8. La session 10 à la session 17 sont des sessions de l’Agent de distribution. La session 18 n’est pas une session de l’Agent de distribution. La session 10 est bloquée par la session 18 et la session 18 est bloquée par la session 11. De plus, la session 10 et la session 11 doivent être validées ensemble. Toutefois, l’Agent de distribution ne peut pas valider la session 10 et la session 11 ensemble en raison du blocage. Par conséquent, l’Agent de distribution ne peut pas coordonner ces huit sessions à valider ensemble tant que la session 10 et la session 11 n’ont pas terminé l’exécution de leurs commandes.

Cet exemple aboutit à un état dans lequel aucune session n’exécute leurs commandes. Lorsque l’heure spécifiée dans la propriété **QueryTimeout** est atteinte, l’Agent de distribution annule toutes les sessions.

> [!Note]
> Par défaut, la valeur de la propriété **QueryTimeout** est de 5 minutes.

Vous remarquerez peut-être les tendances suivantes dans les compteurs de performances de l’Agent de distribution pendant ce délai d’expiration de la requête : 

- La valeur du compteur de performances **Serveur de distribution : commandes livrées/s** est toujours 0.
- La valeur du compteur de performances **Serveur de distribution : transactions livrées/s** est toujours 0.
- Le compteur de performances **Serveur de distribution : latence de livraison** indique une augmentation de la valeur jusqu’à ce que l’interblocage de thread soit résolu.

La rubrique « Agent de distribution de réplication » dans la documentation en ligne de SQL Server contient la description suivante du paramètre *SubscriptionStreams* : « Si l’une des connexions ne parvient pas à s’exécuter ou à valider, toutes les connexions abandonnent le lot actuel et l’agent utilise un seul flux pour retenter les lots ayant échoué ».

L’Agent de distribution utilise une session pour retenter le lot qui n’a pas pu être appliqué. Une fois que l’Agent de distribution applique correctement le lot, il reprend l’utilisation de plusieurs sessions sans avoir à redémarrer.

#### <a name="commitbatchsize"></a>CommitBatchSize
- Augmentez la valeur du paramètre **-CommitBatchSize** pour l’Agent de distribution.  
  
La validation d'un ensemble de transactions comporte une charge fixe ; en validant un grand nombre de transactions moins fréquemment, la charge est répartie sur un volume de données plus important.  L’augmentation de CommitBatchSize (jusqu’à 200) a des chances d’améliorer les performances, car les transactions validées auprès de l’abonné sont plus nombreuses. Cependant, l'avantage obtenu par l'augmentation de ce paramètre disparaît car le coût d'application des modifications est lié à d'autres facteurs, comme l'E/S maximum du disque contenant le journal. Il y a par ailleurs un inconvénient à prendre en compte : en cas de défaillance entraînant le redémarrage de l’Agent de distribution, celui-ci doit se restaurer et réappliquer un grand nombre de transactions. Sur les réseaux non fiables, il peut résulter d’une valeur moins élevée une baisse des défaillances et une diminution du nombre de transactions à restaurer et à réappliquer en cas de défaillance.  
  

## <a name="see-more"></a>En savoir plus
  
[Utiliser des profils d’agent de réplication](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
[Afficher et modifier des paramètres d’invite de commandes d’un Agent de réplication &#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
[Concepts des exécutables de l'agent de réplication](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)  
  
  
