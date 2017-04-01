---
title: "M&#233;moire du serveur (option de configuration de serveur) | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Gestionnaire de mémoire virtuelle"
  - "max server memory (option)"
  - "mémoire virtuelle [SQL Server]"
  - "gestionnaire de mémoire virtuelle"
  - "options de mémoire du serveur [SQL Server]"
  - "serveurs [SQL Server], mémoire"
  - "pools de mémoires tampons [SQL Server]"
  - "min server memory (option)"
  - "options de mémoire manuelles [SQL Server]"
  - "mémoire [SQL Server], serveurs"
ms.assetid: 29ce373e-18f8-46ff-aea6-15bbb10fb9c2
caps.latest.revision: 78
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 78
---
# M&#233;moire du serveur (option de configuration de serveur)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Utilisez les deux options de mémoire du serveur, **min server memory** et **max server memory**, pour reconfigurer la quantité de mémoire (en mégaoctets) gérée par le Gestionnaire de mémoire de SQL Server pour un processus SQL Server utilisé par une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Le paramètre par défaut de l'option **min server memory** est 0 et le paramètre par défaut de l'option **max server memory** est 2 147 483 647 Mo. Par défaut, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut modifier dynamiquement sa configuration mémoire en fonction des ressources système disponibles.  
  
> [!NOTE]  
>  Si vous donnez à **max server memory** sa valeur minimale, vous allez gravement limiter les performances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , jusqu'à l'empêcher même de démarrer. Si vous ne pouvez plus démarrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] après avoir changé cette option, démarrez-le au moyen de l’option de démarrage **–f** et restaurez **max server memory** à sa valeur antérieure. Pour plus d’informations, consultez [Options de démarrage du service moteur de base de données](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
 Lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise dynamiquement la mémoire, il interroge régulièrement le système afin de déterminer la mémoire physique disponible. La conservation de cette mémoire libre empêche le système d'exploitation de paginer. S'il y a moins de mémoire, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en libère pour le système d'exploitation. S’il y a plus de mémoire disponible, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut allouer davantage de mémoire. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’ajoute de la mémoire que lorsque sa charge de travail en requiert davantage. Un serveur au repos n’augmente pas la taille de son espace d’adressage virtuel.  
  
 Pour une requête qui retourne la mémoire utilisée actuellement, consultez l'exemple B. L’option **max server memory** contrôle l’allocation de mémoire de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], y compris le pool de mémoires tampons, la mémoire de compilation, tous les caches, les allocations de mémoire qe, la mémoire du gestionnaire de verrous et la mémoire clr (essentiellement les régisseurs de mémoires qui se trouvent dans **sys.dm_os_memory_clerks**). La mémoire pour les piles de threads, les segments de mémoire, les fournisseurs de serveurs liés autres que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ainsi que toute mémoire allouée par une DLL non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ne sont pas contrôlées par max server memory.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise l'API de notification de mémoire **QueryMemoryResourceNotification** pour déterminer le moment où le Gestionnaire de mémoire de SQL Server peut allouer et libérer de la mémoire.  
  
 Il est recommandé de permettre à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d'utiliser dynamiquement la mémoire ; cependant, vous pouvez configurer manuellement les options de mémoire et limiter la mémoire à laquelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut accéder. Avant de définir la mémoire allouée à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], déterminez la valeur adaptée pour la mémoire : pour cela, vous devez soustraire de la mémoire physique totale la mémoire requise par le système d'exploitation et par toute autre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], (ainsi que par d'autres systèmes si l'ordinateur n'est pas totalement dédié à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]). Cette différence représente la mémoire maximale que vous pouvez allouer à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Paramétrage manuel des options de mémoire  
 Définissez **min server memory** et **max server memory** afin de couvrir une plage de valeurs de mémoire. Cette méthode est utile pour les administrateurs système ou de bases de données qui souhaitent configurer une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en accord avec la mémoire requise par les autres applications exécutées sur le même ordinateur.  
  
 Utilisez l'option **min server memory** pour garantir une quantité minimale de mémoire disponible pour le Gestionnaire de mémoire de SQL Server pour une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'alloue pas immédiatement la mémoire spécifiée dans **min server memory** au démarrage. Néanmoins, lorsque l’utilisation de la mémoire atteint cette valeur en raison de la charge client, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut libérer de la mémoire à moins que la valeur **min server memory** ne soit réduite.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alloue la mémoire spécifiée dans **min server memory**. Si la charge sur le serveur ne nécessite jamais d’allouer la mémoire spécifiée dans **min server memory**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’exécute alors avec moins de mémoire.  
  
 La taille mémoire minimale autorisée pour **max server memory** est de 128 Mo.  
  
## Comment configurer les options de mémoire à l'aide de SQL Server Management Studio  
 Utilisez les deux options de mémoire du serveur, **min server memory** et **max server memory**, pour reconfigurer la quantité de mémoire (en mégaoctets) gérée par le Gestionnaire de mémoire de SQL Server pour une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par défaut, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut modifier dynamiquement sa configuration mémoire en fonction des ressources système disponibles.  
  
### Procédure de configuration d'une quantité de mémoire fixe  
 Pour définir une quantité fixe de mémoire  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur un serveur et sélectionnez **Propriétés**.  
  
2.  Cliquez sur le nœud **Mémoire** .  
  
3.  Sous **Options mémoire du serveur**, entrez les quantités souhaitées pour **Mémoire minimale du serveur** et **Mémoire maximale du serveur**.  
  
     Utilisez les paramètres par défaut pour autoriser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à modifier ses besoins de mémoire de façon dynamique en fonction des ressources système disponibles. Le paramètre par défaut de l’option **min server memory** est 0 et le paramètre par défaut de l’option **max server memory** est 2147483647 mégaoctets (Mo).  
  
## Obtenir le débit de données maximal pour les applications réseau  
 Pour optimiser l'utilisation de la mémoire système pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez limiter la quantité de mémoire utilisée par le système pour la mise en cache des fichiers. Pour limiter le cache du système de fichiers, veillez à désactiver **Maximiser le débit des données pour le partage de fichiers** . Vous pouvez spécifier le plus petit cache du système de fichiers en sélectionnant **Minimiser la mémoire utilisée** ou **Équilibrer**.  
  
#### Pour connaître la configuration actuelle de votre système d'exploitation  
  
1.  Cliquez sur **Démarrer**, sur **Panneau de configuration**, double-cliquez sur **Connexions réseau**, puis sur **Connexion au réseau local**.  
  
2.  Sous l'onglet **Général** , cliquez sur **Propriétés**. Sélectionnez **Partage de fichiers et d'imprimantes pour les réseaux Microsoft**et cliquez sur **Propriétés**.  
  
3.  Si l'option **Maximiser le débit des données pour les applications réseau** est sélectionnée, choisissez une autre option et cliquez sur **OK**. Fermez ensuite les boîtes de dialogue restantes.  
  
## Verrouiller les pages en mémoire  
 Cette stratégie Windows détermine quels comptes peuvent utiliser un processus destiné à conserver les données en mémoire physique pour éviter leur pagination en mémoire virtuelle sur le disque. Le verrouillage des pages en mémoire peut permettre de conserver sa réactivité au serveur lors de la pagination de la mémoire sur disque. L’option SQL Server **Verrouiller les pages en mémoire** a la valeur ON dans les instances de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] éditions Standard et supérieures quand le compte avec les privilèges nécessaires pour exécuter sqlservr.exe a reçu le droit d’utilisateur Windows de verrouillage des pages en mémoire (LPIM, Locked Pages in Memory).  
  
 Pour désactiver l'option **Verrouiller les pages en mémoire** pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], supprimez le droit d'utilisateur de verrouillage des pages en mémoire pour le compte de démarrage de SQL Server.  
  
### Pour désactiver Verrouiller les pages en mémoire  
 Pour désactiver l'option Verrouiller les pages en mémoire  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**. Dans la zone **Ouvrir** , tapez **gpedit.msc**  
  
     La boîte de dialogue **Stratégie de groupe** s'affiche.  
  
2.  Sur la console **Stratégie de groupe** , développez **Configuration de l'ordinateur**, puis **Paramètres Windows**.  
  
3.  Développez **Paramètres de sécurité**, puis **Stratégies locales**.  
  
4.  Sélectionnez le dossier **Attribution des droits utilisateur** .  
  
     Les stratégies s'affichent dans le volet Détails.  
  
5.  Dans le volet, double-cliquez sur **Verrouiller les pages en mémoire**.  
  
6.  Dans la boîte de dialogue **Paramètre de stratégie de sécurité locale** , sélectionnez le compte avec les privilèges nécessaires pour exécuter sqlservr.exe et cliquez sur **Supprimer**.  
  
## Gestionnaire de mémoire virtuelle  
 Les zones d'espace d'adressage validées sont mappées à la mémoire physique disponible par le Gestionnaire de mémoire virtuelle Windows (VMM).  
  
 Pour plus d'informations sur la taille de mémoire physique prise en charge par les divers systèmes d'exploitation, consultez la documentation Windows « Limites de la mémoire selon les versions de Windows ».  
  
 Les systèmes de mémoire virtuelle autorisent le surengagement de la mémoire physique, de sorte que le rapport entre la mémoire virtuelle et la mémoire physique peut être supérieur à 1:1. Il est alors possible d'exécuter des programmes plus volumineux sur des ordinateurs offrant diverses configurations de la mémoire physique. Toutefois, dans la plupart des cas, l'utilisation d'une quantité de mémoire virtuelle nettement plus importante que les plages de travail moyennes combinées de tous les processus peut entraîner une détérioration des performances.  
  
 **min server memory** et **max server memory** sont des options avancées. Si vous utilisez la procédure stockée système **sp_configure** pour changer ces paramètres, vous ne pouvez les modifier que si l’option **show advanced options** a la valeur 1. Ces paramètres entrent immédiatement en vigueur, sans redémarrage du serveur.  
  
## Exécution de plusieurs instances SQL Server  
 Lorsque vous exécutez plusieurs instances de [!INCLUDE[ssDE](../../includes/ssde-md.md)], vous avez le choix entre trois approches pour gérer la mémoire :  
  
-   Choisir **max server memory** pour contrôler l'utilisation de la mémoire. Définir les valeurs maximales pour chaque instance, en veillant à ce que le total alloué ne soit pas supérieur à la mémoire physique totale de votre ordinateur. Il se peut que vous souhaitiez attribuer à chaque instance une mémoire proportionnelle à la charge ou à la taille de base de données prévue. Cette solution présente l'avantage qu'au démarrage des nouveaux processus ou des nouvelles instances, ils pourront accéder immédiatement à la mémoire libre. En revanche, cette solution présente l'inconvénient que, si toutes les instances ne sont pas en cours d'exécution, aucune d'entre elles ne pourra utiliser la mémoire libre restante.  
  
-   Choisir **min server memory** pour contrôler l'utilisation de la mémoire. Définissez les valeurs minimales pour chaque instance, de telle sorte que leur somme soit inférieure de 1 à 2 Go à la mémoire physique totale de votre machine. Une fois encore, vous pouvez établir ces valeurs minimales de façon proportionnelle à la charge prévue de cette instance. Cette solution présente l'avantage que si toutes les instances ne sont pas en cours d'exécution au même instant, celles qui le sont peuvent utiliser la mémoire libre restante. Elle est également utile quand un autre processus gourmand en mémoire est présent sur l'ordinateur, car elle garantit que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bénéficie au moins d'une quantité de mémoire acceptable. Le désagrément est que, lorsqu'une nouvelle instance (ou un autre processus) démarre, il se peut que les instances en cours d'exécution mettent un certain temps à libérer de la mémoire, notamment si elles doivent à cette fin réécrire les pages modifiées sur leurs bases de données.  
  
-   Ne rien faire (déconseillé). Les premières instances présentées avec une charge de travail tendent à allouer la totalité de la mémoire. Les instances inactives ou les instances ayant démarré ultérieurement peuvent finir par ne disposer que d'une quantité de mémoire minime. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'effectue aucune tentative pour équilibrer l'utilisation de la mémoire entre les instances. Cependant, toutes les instances répondent aux signaux de Windows Notification Memory pour ajuster la taille de leur occupation mémoire. Windows n'équilibre pas la mémoire entre les applications avec l'API Memory Notification. Il fournit simplement un commentaire global quant à la disponibilité de la mémoire sur le système.  
  
 Comme vous pouvez modifier ces paramètres sans redémarrer les instances, vous pouvez sans peine procéder à des essais pour trouver les valeurs qui conviennent le mieux à votre modèle d'utilisation.  
  
## Apport de la quantité maximale de mémoire à SQL Server  
 La mémoire peut être configurée jusqu’à la limite de l’espace d’adressage virtuel utilisé par le processus dans toutes les éditions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (8 To).  
  
 ***/3gb** est un paramètre d’amorçage de système d’exploitation. Pour plus d'informations, consultez [MSDN Library](http://go.microsoft.com/fwlink/?LinkID=10257&clcid=0x409)(en anglais).  
  
## Exemples  
  
### Exemple A  
 L'exemple suivant affecte la valeur 4 Go à l'option `max server memory` .  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'max server memory', 4096;  
GO  
RECONFIGURE;  
GO  
```  
  
### Exemple B. Détermination de l’allocation de mémoire actuelle  
 La requête suivante retourne des informations sur la mémoire allouée actuellement.  
  
```  
SELECT  
(physical_memory_in_use_kb/1024) AS Memory_usedby_Sqlserver_MB,  
(locked_page_allocations_kb/1024) AS Locked_pages_used_Sqlserver_MB,  
(total_virtual_address_space_kb/1024) AS Total_VAS_in_MB,  
process_physical_memory_low,  
process_virtual_memory_low  
FROM sys.dm_os_process_memory;  
```  
  
## Voir aussi  
 [Surveiller et régler les performances](../../relational-databases/performance/monitor-and-tune-for-performance.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  