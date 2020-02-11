---
title: Options de configuration du serveur (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 02/29/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- surface area configuration [SQL Server], sp_configure
- configuration options [SQL Server], when take effect
- server management [SQL Server], configuration options
- SQL Server Management Studio [SQL Server], servers
- servers [SQL Server], configuring
- configuration options [SQL Server], setting
- options [SQL Server], configuration
- RECONFIGURE statement
- performance [SQL Server], servers
- configuration options [SQL Server]
- RECONFIGURE WITH OVERRIDE statement
- SQL Server, configuring
- sp_configure
- stored procedures [SQL Server], configuration options
- server configuration [SQL Server]
- administering SQL Server, configuration options
ms.assetid: 9f38eba6-39b1-4f1d-ba24-ee4f7e2bc969
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 645aee1374f7dbf3c290500bb35ca47115983670
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62809567"
---
# <a name="server-configuration-options-sql-server"></a>Options de configuration du serveur (SQL Server)
  Vous pouvez gérer et optimiser les ressources de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par le bais des options de configuration, en utilisant soit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , soit la procédure stockée système sp_configure. Les options de configuration de serveur les plus fréquemment utilisées sont accessibles via [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]; toutes les options de configuration sont accessibles via sp_configure. Avant de paramétrer ces options, vous devez tenir compte de leurs conséquences sur votre système. Pour plus d’informations, consultez [Afficher ou modifier des propriétés de serveur &#40;SQL Server&#41;](view-or-change-server-properties-sql-server.md)  
  
> [!IMPORTANT]  
>  Les options avancées ne doivent être modifiées que par un administrateur de base de données qualifié ou un technicien agréé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="categories-of-configuration-options"></a>Catégories d'options de configuration  
 Les options de configuration prennent effet :  
  
-   immédiatement après la définition de l'option et l'émission de l'instruction RECONFIGURE (ou dans certains cas, de l'instruction RECONFIGURE WITH OVERRIDE) ;  
  
     -ou-  
  
-   Après avoir effectué les actions ci-dessus et redémarré l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Les options qui nécessitent un redémarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affichent initialement la valeur modifiée uniquement dans la colonne value. Après le redémarrage, la nouvelle valeur apparaîtra dans la colonne value et la colonne value_in_use.  
  
 Certaines options nécessitent l'arrêt du serveur afin que la nouvelle valeur soit prise en considération. Si vous définissez la nouvelle valeur et exécutez sp_configure avant de redémarrer le serveur, la nouvelle valeur apparaîtra dans la colonne value des options de configuration, mais elle ne figurera pas dans la colonne value_in_use. Après le redémarrage du serveur, la nouvelle valeur apparaît dans la colonne value_in_use.  
  
 Les options à configuration automatique correspondent aux options que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] règle en fonction des besoins du système. Dans la plupart des cas, il est inutile de définir les valeurs manuellement. À titre d'exemple, nous pouvons citer les options min server memory et max server memory, ainsi que l'option user connections.  
  
## <a name="configuration-options-table"></a>Tableau des options de configuration  
 Le tableau ci-après dresse la liste des options de configuration disponibles et indique leurs plages de paramétrage possible ainsi que leurs valeurs par défaut. Les options de configuration sont signalées par des codes sous forme de lettres, comme suit :  
  
-   A = Options avancées, c'est-à-dire les options qui ne peuvent être modifiées que par un administrateur de base de données qualifié ou un technicien agréé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , et pour lesquelles l'option show advanced options doit être définie sur 1.  
  
-   RR = Options qui nécessitent un redémarrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
-   SC = Options à configuration automatique.  
  
    |Option de configuration|Valeur minimale|Valeur maximale|Default|  
    |--------------------------|-------------------|-------------------|-------------|  
    |[nombre de compartiments du cache de vérification d’accès](access-check-cache-server-configuration-options.md) (A)|0|16 384|0|  
    |[quota de vérification de l’accès cache](access-check-cache-server-configuration-options.md) (A)|0|2147483647|0|  
    |[requêtes distribuées ad hoc](ad-hoc-distributed-queries-server-configuration-option.md) (A)|0|1|0|  
    |[Affinity I/O mask](affinity-input-output-mask-server-configuration-option.md) (A, RR)|-2147483648|2147483647|0|  
    |[affinity64 I/O mask](affinity64-input-output-mask-server-configuration-option.md) (A, uniquement disponible sur la version 64 bits de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])|-2147483648|2147483647|0|  
    |[affinity mask](affinity-mask-server-configuration-option.md) (A)|-2147483648|2147483647|0|  
    |[affinity64 mask](affinity64-mask-server-configuration-option.md) (A, RR), uniquement disponible sur la version 64 bits de[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|-2147483648|2147483647|0|  
    |[Agent XPS](agent-xps-server-configuration-option.md) (A)|0|1|0<br /><br /> (Prend la valeur 1 au démarrage de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . La valeur par défaut est 0 si l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré pour démarrer automatiquement pendant l'installation.)|  
    |[autoriser les mises à jour](allow-updates-server-configuration-option.md) (obsolète. Ne pas utiliser. Provoquera une erreur lors de la reconfiguration.)|0|1|0|  
    |[paramètre par défaut de la somme de contrôle de sauvegarde](../backup-checksum-default.md)|0|1|0|  
    |[compression de la sauvegarde par défaut](view-or-configure-the-backup-compression-default-server-configuration-option.md)|0|1|0|  
    |[seuil de processus bloqué](blocked-process-threshold-server-configuration-option.md) (A)|0|86400|0|  
    |[mode d’audit C2](c2-audit-mode-server-configuration-option.md) (A, RR)|0|1|0|  
    |[clr enabled](clr-enabled-server-configuration-option.md)|0|1|0|  
    |[conformité aux critères communs activée](common-criteria-compliance-enabled-server-configuration-option.md) (A, RR)|0|1|0|  
    |[authentification de la base de données autonome](contained-database-authentication-server-configuration-option.md)|0||0|  
    |[seuil de coût pour le parallélisme](configure-the-cost-threshold-for-parallelism-server-configuration-option.md) (A)|0|32767|5|  
    |[cross db ownership chaining](cross-db-ownership-chaining-server-configuration-option.md)|0|1|0|  
    |[seuil du curseur](configure-the-cursor-threshold-server-configuration-option.md) (A)|-1|2147483647|-1|  
    |[Database mail XPS](database-mail-xps-server-configuration-option.md) (A)|0|1|0|  
    |[langue de texte intégral par défaut](configure-the-default-full-text-language-server-configuration-option.md) (A)|0|2147483647|1033|  
    |[langue par défaut](configure-the-default-language-server-configuration-option.md)|0|9 999|0|  
    |[trace par défaut activée](default-trace-enabled-server-configuration-option.md) (A)|0|1|1|  
    |[interdire les résultats à partir des déclencheurs](disallow-results-from-triggers-server-configuration-option.md) (A)|0|1|0|  
    |[Fournisseur EKM activé](ekm-provider-enabled-server-configuration-option.md)|0|1|0|  
    |[filestream_access_level](filestream-access-level-server-configuration-option.md)|0|2|0|  
    |[facteur de remplissage](configure-the-fill-factor-server-configuration-option.md) (A, RR)|0|100|0|  
    |ft crawl bandwidth (max), consultez [ft crawl bandwidth](ft-crawl-bandwidth-server-configuration-option.md)(A)|0|32767|100|  
    |ft crawl bandwidth (min), consultez [ft crawl bandwidth](ft-crawl-bandwidth-server-configuration-option.md)(A)|0|32767|0|  
    |ft notify bandwidth (max), consultez [ft notify bandwidth](ft-notify-bandwidth-server-configuration-option.md)(A)|0|32767|100|  
    |ft notify bandwidth (min), consultez [ft notify bandwidth](ft-notify-bandwidth-server-configuration-option.md)(A)|0|32767|0|  
    |[création d’index en mémoire](configure-the-index-create-memory-server-configuration-option.md) (A, SC)|704|2147483647|0|  
    |[résolution des transactions incertaines](in-doubt-xact-resolution-server-configuration-option.md) (A)|0|2|0|  
    |[regroupement léger](lightweight-pooling-server-configuration-option.md) (A, RR)|0|1|0|  
    |[verrous](configure-the-locks-server-configuration-option.md) (A, RR, SC)|5 000|2147483647|0|  
    |[degré maximal de parallélisme](configure-the-max-degree-of-parallelism-server-configuration-option.md) (A)|0|32767|0|  
    |[plage de l’analyse de texte intégral Max](max-full-text-crawl-range-server-configuration-option.md) (A)|0|256|4|  
    |[Max Server Memory](server-memory-server-configuration-options.md) (A, SC)|16|2147483647|2147483647|  
    |[max text repl size](configure-the-max-text-repl-size-server-configuration-option.md)|0|2147483647|65536|  
    |[nombre maximal de threads de travail](configure-the-max-worker-threads-server-configuration-option.md) (A)|128|32767<br /><br /> (1 024 correspond au maximum recommandé pour la version 32 bits de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et 2 048 pour la version 64 bits de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)|0<br /><br /> Zéro configure automatiquement le nombre maximal de threads de travail en fonction du nombre de processeurs, à l’aide de la formule (256 + (*\<processeurs>* -4) * 8) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour 32 bits et deux fois pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]64 bits.|  
    |[rétention de support](configure-the-media-retention-server-configuration-option.md) (A, RR)|0|365|0|  
    |[mémoire minimum par requête](configure-the-min-memory-per-query-server-configuration-option.md) (A)|512|2147483647|1 024|  
    |[min Server Memory](server-memory-server-configuration-options.md) (A, SC)|0|2147483647|0|  
    |[déclencheurs imbriqués](configure-the-nested-triggers-server-configuration-option.md)|0|1|1|  
    |[taille du paquet réseau](configure-the-network-packet-size-server-configuration-option.md) (A)|512|32767|4096|  
    |[Procédures OLE Automation](ole-automation-procedures-server-configuration-option.md) (A)|0|1|0|  
    |[objets ouverts](open-objects-server-configuration-option.md) (A, RR, obsolète)|0|2147483647|0|  
    |[optimiser pour les charges de travail ad hoc](optimize-for-ad-hoc-workloads-server-configuration-option.md) (A)|0|1|0|  
    |[PH_timeout](ph-timeout-server-configuration-option.md) (A)|1|3600|60|  
    |[précalculer le rang](precompute-rank-server-configuration-option.md) (A)|0|1|0|  
    |[renforcement de priorité](configure-the-priority-boost-server-configuration-option.md) (A, RR)|0|1|0|  
    |[limite de coût](configure-the-query-governor-cost-limit-server-configuration-option.md) de l’administrateur de requêtes (A)|0|2147483647|0|  
    |[attente de requête](configure-the-query-wait-server-configuration-option.md) (A)|-1|2147483647|-1|  
    |[intervalle de récupération](configure-the-recovery-interval-server-configuration-option.md) (A, SC)|0|32767|0|  
    |[accès à distance](configure-the-remote-access-server-configuration-option.md) (RR)|0|1|1|  
    |[remote admin connections](remote-admin-connections-server-configuration-option.md)|0|1|0|  
    |[délai d’attente de la connexion distante](configure-the-remote-login-timeout-server-configuration-option.md)|0|2147483647|10|  
    |[transaction de procédure distante](configure-the-remote-proc-trans-server-configuration-option.md)|0|1|0|  
    |[remote query timeout](configure-the-remote-query-timeout-server-configuration-option.md)|0|2147483647|600|  
    |[Option de réplication XPS](replication-xps-server-configuration-option.md) (A)|0|1|0|  
    |[Rechercher les procédures de démarrage](configure-the-scan-for-startup-procs-server-configuration-option.md) (A, RR)|0|1|0|  
    |[server trigger recursion](server-trigger-recursion-server-configuration-option.md)|0|1|1|  
    |[définir la taille](set-working-set-size-server-configuration-option.md) de la plage de travail (A, RR, obsolète)|0|1|0|  
    |[show advanced options](show-advanced-options-server-configuration-option.md)|0|1|0|  
    |[Smo et DMO XPS](smo-and-dmo-xps-server-configuration-option.md) (A)|0|1|1|  
    |[transformer les mots parasites](transform-noise-words-server-configuration-option.md) (A)|0|1|0|  
    |[année de coupure à deux chiffres](configure-the-two-digit-year-cutoff-server-configuration-option.md) (A)|1753|9 999|2049|  
    |[connexions utilisateur](configure-the-user-connections-server-configuration-option.md) (A, RR, SC)|0|32767|0|  
    |[user options](configure-the-user-options-server-configuration-option.md)|0|32767|0|  
    |[xp_cmdshell](xp-cmdshell-server-configuration-option.md) (A)|0|1|0|  
  
## <a name="see-also"></a>Voir aussi  
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
