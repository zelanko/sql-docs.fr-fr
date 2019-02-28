---
title: Configurer replay dans l’Assistant expérimentation de base de données pour les mises à niveau de SQL Server
description: Configuration de relecture dans l’Assistant expérimentation de base de données
ms.custom: ''
ms.date: 10/22/2018
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: ajaykar
ms.reviewer: douglasl
manager: craigg
ms.openlocfilehash: 76516c02b03443ca6c7642f75c16cf53b07b3e8a
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "56987785"
---
# <a name="configure-replay-in-database-experimentation-assistant"></a>Configuration de relecture dans l’Assistant expérimentation de base de données

L’Assistant base de données expérimentation (DEA) utilise les outils de Distributed Replay à partir de l’installation de SQL Server pour relire une trace capturée sur un environnement de test mis à niveau. Nous vous recommandons d’effectuer une série à l’aide d’un fichier de trace petites avant d’effectuer une relecture complète pour garantir la relecture correcte des requêtes de tests.

## <a name="distributed-replay-requirements"></a>Conditions préalables de relecture distribuées

- Un supplémentaire 78 % d’espace de disque dur est nécessaire pour créer des fichiers HAPLOTYPES IRF sur l’ordinateur du contrôleur Distributed Replay.
- 200 Mo ou 512 Mo est la taille de la substitution de trace idéale à utiliser pour capturer des traces de production ou de performances.   
- La configuration minimale du processeur et mémoire RAM requise pour les machines de Distributed Replay controller et client est un processeur monocœur avec 3,5 Go de RAM.
- Heure de relecture prend environ 1,55 fois plus longtemps que le temps de capture, car un seul contrôleur et quatre ordinateurs enfants sont utilisés pour relire la trace de production.
- Si vous utilisez nos versions « publiées » de production et les fichiers de définition de trace de performances et les performances trace définition exclut les traces pour une base de données d’intérêt, analyse montre que le **performances Trace** est de taille environ 15 fois supérieure à la **Trace de Production** taille.

## <a name="set-up-a-virtual-network-or-domain"></a>Configurer un réseau virtuel ou un domaine

Distributed Replay, vous devez utiliser des comptes communs entre les machines. En raison de cette exigence et pour des raisons de sécurité, nous vous recommandons de Distributed Replay en cours d’exécution sur un réseau virtuel ou sur un réseau contrôlé par domaine :

- Créer le contrôleur et le client machines dans l’environnement.
- Assurez-vous que les contrôleur et les machines clientes peuvent communiquer entre elles sur le réseau.
- Les ordinateurs de clients de relecture distribuées doivent être connectés à l’ordinateur cible de la relecture SQL Server en cours d’exécution.

## <a name="set-up-the-controller-service"></a>Configurer le service de contrôleur

Pour configurer le service de contrôleur :

1. Installer le contrôleur de Distributed Replay à l’aide du programme d’installation de SQL Server. Si vous avez ignoré l’étape de l’Assistant programme d’installation de SQL Server qui configure le contrôleur Distributed Replay, vous pouvez configurer le contrôleur via le fichier de configuration. Dans une installation par défaut, le fichier de configuration se trouve dans C:\Program Files (x86) \Microsoft SQL Server\<version\>\Tools\DReplayController\DReplayController.config.
1. Journaux du contrôleur Distributed Replay sont trouvent dans C:\Program Files (x86) \Microsoft SQL Server\<version\>\Tools\DReplayController\Log.
1. Ouvrez Services.msc et accédez à la **SQL Server Distributed Replay Controller** service.
1. Avec le bouton droit sur le service, puis sélectionnez **propriétés**. Définissez le compte de service sur un compte qui est courant pour les machines de contrôleur et le client dans le réseau.
1. Sélectionnez **OK** pour fermer la **propriétés** fenêtre.
1. Redémarrez le **SQL Server Distributed Replay Controller** service à partir de Services.msc. Vous pouvez également exécuter les commandes suivantes sur la ligne de commande pour redémarrer le service :<br/>
   `NET STOP "SQL Server Distributed Replay Controller"`<br/>
   `NET START "SQL Server Distributed Replay Controller"`
1. Pour les autres options de configuration, consultez [configurer Distributed Replay](https://docs.microsoft.com/sql/tools/distributed-replay/configure-distributed-replay).

## <a name="configure-dcom"></a>Configurer DCOM

Cette configuration est requis uniquement sur l’ordinateur du contrôleur.

1. Ouvrez dcomcnfg.exe.
1. Développez **Services de composants** > **ordinateurs** > **mon ordinateur** > **configuration DCOM**.
1. Sous **configuration DCOM**, avec le bouton droit **DReplayController**, puis sélectionnez **propriétés**.
1. Sélectionnez l'onglet **Sécurité** .
1. Sous **autorisations d’exécution et d’Activation**, sélectionnez **personnaliser**, puis sélectionnez **modifier**.
1. Ajoutez l’utilisateur qui entreront en la relecture. Accordez à l’utilisateur les autorisations d’exécution locale et Activation locale. Si l’utilisateur prévoit de lancer ou activer à distance, accordez les autorisations de lancement à distance et Activation à distance à l’utilisateur.
1. Sélectionnez **OK** pour valider les modifications et revenir à la **sécurité** onglet.
1. Sous **autorisations d’accès**, sélectionnez **personnaliser**, puis sélectionnez **modifier**.
1. Ajoutez l’utilisateur qui entreront en la relecture. Accordez à l’utilisateur les autorisations d’accès Local. Si l’utilisateur souhaite accéder au service de contrôleur à distance, accordez les autorisations d’accès à distance à l’utilisateur.
1. Sélectionnez **OK** pour valider les modifications et revenir à la **sécurité** onglet.
1. Sélectionnez **OK** pour valider les modifications.
1. Redémarrez le service SQL Server Distributed Replay Controller à partir de Services.msc. Vous pouvez également exécuter les commandes suivantes sur la ligne de commande pour redémarrer le service :<br/>
   `NET STOP "SQL Server Distributed Replay Controller"`<br/>
   `NET START "SQL Server Distributed Replay Controller"`

## <a name="set-up-the-client-service"></a>Configurer le service client

Avant de configurer le service client, utilisez la mise en réseau des outils tels que ping pour vérifier que les contrôleur et les machines clientes peuvent communiquer.

1. Installer le client de Distributed Replay à l’aide du programme d’installation de SQL Server.
1. Ouvrez Services.msc et accédez au service SQL Server Distributed Replay Client.
1. Avec le bouton droit sur le service, puis sélectionnez **propriétés**. Définissez le compte de service sur un compte qui est commun aux ordinateurs à la fois le contrôleur et le client dans le réseau.
1. Sélectionnez **OK** pour fermer la **propriétés** fenêtre. Si vous avez ignoré l’étape de l’Assistant programme d’installation de SQL Server pour configurer le client de Distributed Replay, vous pouvez la configurer via le fichier de configuration. Dans une installation par défaut, le fichier de configuration se trouve dans C:\Program Files (x86) \Microsoft SQL Server\<version\>\Tools\DReplayClient\DReplayClient.config.
1. Assurez-vous que le fichier DReplayClient.config contient le nom de l’ordinateur du contrôleur en tant que son contrôleur pour l’inscription.
1.  Redémarrez le service SQL Server Distributed Replay Client à partir de Services.msc. Vous pouvez également exécuter les commandes suivantes à partir de la ligne de commande pour redémarrer le service :<br/>
    `NET STOP "SQL Server Distributed Replay Client"`<br/>
    `NET START "SQL Server Distributed Replay Client"`
1. Journaux du contrôleur Distributed Replay sont trouvent dans C:\Program Files (x86) \Microsoft SQL Server\<version\>\Tools\DReplayClient\Log. Les journaux indiquent si le client peut s’inscrire auprès du contrôleur.
1. Si la configuration a réussi, le journal affiche le message « inscrit avec le contrôleur < nom du contrôleur\>».
1. Pour les autres options de configuration, consultez [configurer Distributed Replay](https://docs.microsoft.com/sql/tools/distributed-replay/configure-distributed-replay).

## <a name="set-up-distributed-replay-administration-tools"></a>Configurer les outils d’administration Distributed Replay

Vous pouvez utiliser les outils d’administration Distributed Replay pour tester rapidement le fonctionnement de Distributed Replay dans l’environnement. Peut être particulièrement utile dans un environnement dans lequel plusieurs ordinateurs clients sont inscrits auprès d’un contrôleur de test de la configuration. Vous devrez peut-être installer SQL Server Management Studio (SSMS) pour obtenir les outils d’administration.

1. Accédez à SSMS emplacement d’installation et recherchez le Distributed Replay administration outil dreplay.exe et ses composants dépendants.
1. Ouvrez une fenêtre d’invite de commandes et exécutez `dreplay.exe status -f 1`.
1. Si toutes les étapes précédentes sont réussies, la sortie de console indique que le contrôleur peut voir ses clients dans un `READY` état.

## <a name="configure-the-firewall-for-remote-distributed-replay-access"></a>Configurer le pare-feu pour l’accès à distance de Distributed Replay

L’accès à distance de Distributed Replay requiert l’ouverture des ports qui sont visibles dans le domaine ou le réseau virtuel.

1. Ouvrez **Windows Firewall** avec **fonctions avancées de sécurité**.
1. Accédez à **règles de trafic entrant**.
1. Créer une nouvelle règle de pare-feu entrante pour le programme C:\Program Files (x86) \Microsoft SQL Server\<version\>\Tools\DReplayController\DReplayController.exe.
1. Autoriser l’accès au niveau du domaine pour tous les ports pour DReplayController.exe être en mesure de communiquer avec le service de contrôleur à distance.
1. Enregistrer la règle.

## <a name="set-up-target-computers"></a>Configurer les ordinateurs cibles

Deux des relectures sont nécessaires pour exécuter un A / test de B ou d’une expérience. Autrement dit, vous devrez peut-être les deux instances distinctes d’installations de SQL Server pour un scénario de migration. 

Vous pouvez également installer les deux versions d’instances de SQL Server sur le même ordinateur. Un inconvénient consiste à s’assurer que les instances sont complètement isolés lorsqu’une relecture est en cours.

Les étapes suivantes doivent être effectuées pour chaque relecture :

1. Restaurez la sauvegarde de la base de données.
1. Accorder des autorisations pour l’utilisateur du compte de service client accéder aux bases de données sous l’instance de SQL Server. Les autorisations sont requises pour les requêtes à exécuter sur l’instance de SQL Server.
1. Démarrer la relecture.

## <a name="next-steps"></a>Étapes suivantes

- Pour savoir comment relire une trace capturée dans un environnement de test mis à niveau, consultez [relire la trace](database-experimentation-assistant-replay-trace.md).

- Pour une présentation 19 minutes DEA et de démonstration, regardez la vidéo suivante :

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
