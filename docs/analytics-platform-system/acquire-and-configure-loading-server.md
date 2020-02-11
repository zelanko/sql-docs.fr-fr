---
title: Acquérir & configurer le chargement du serveur
description: Cet article explique comment acquérir et configurer un serveur de chargement comme système Windows non-appareil pour soumettre des chargements de données à des Data Warehouse parallèles (PDW).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: ef49bb86c8e16600f2ff1bf2d1c7a92ecc5af964
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401485"
---
# <a name="acquire-and-configure-a-loading-server-for-parallel-data-warehouse"></a>Acquérir et configurer un serveur de chargement pour les Data Warehouse parallèles
Cet article explique comment acquérir et configurer un serveur de chargement comme système Windows non-appareil pour soumettre des chargements de données à des Data Warehouse parallèles (PDW).  
  
## <a name="Basics"></a>Fondamentaux  
Le serveur de chargement :  
  
-   Ne doit pas nécessairement être un serveur unique. Vous pouvez charger en même temps avec plusieurs serveurs de chargement.  
  
-   Est fourni et géré par votre propre équipe informatique. Vous disposez peut-être déjà d’un serveur ou de serveurs qui peuvent être utilisés pour le chargement de données dans PDW.  
  
-   Se trouve dans votre propre rack non-appliance et ne peut pas être placé dans l’appliance Analytics Platform System.  
  
-   Est connecté à l’appliance via le réseau de l’appliance InfiniBand ou sur Ethernet. Pour des performances optimales, nous vous recommandons d’utiliser InfiniBand.  
  
-   Se trouve dans votre propre domaine de client, et non dans le domaine de l’appliance. Il n’existe aucune relation d’approbation entre votre domaine client et le domaine de l’appliance.  
  
## <a name="Step1"></a>Étape 1 : déterminer les besoins en capacité  
Le système de chargement peut être conçu comme un ou plusieurs serveurs de chargement qui effectuent des chargements simultanés. Il n’est pas nécessaire que chaque serveur de chargement soit dédié au chargement, à condition qu’il gère les besoins en termes de performances et de stockage de votre charge de travail.  
  
La configuration système requise pour un serveur de chargement dépend presque entièrement de votre propre charge de travail. Utilisez la [feuille de calcul de planification de la capacité du serveur](loading-server-capacity-planning-worksheet.md) pour déterminer vos besoins en capacité.  
  
## <a name="Step2"></a>Étape 2 : acquérir le Server  
Maintenant que vous comprenez mieux vos besoins en matière de capacité, vous pouvez planifier les serveurs et les composants de mise en réseau que vous devrez acheter ou approvisionner. Incorporez la liste suivante d’exigences dans votre plan d’achat, puis achetez votre serveur ou approvisionnez un serveur existant.  
  
### <a name="R"></a>Configuration logicielle requise  
Systèmes d'exploitation pris en charge :  
  
-   Windows Server 2012 ou Windows Server 2012 R2. Ces systèmes d’exploitation nécessitent la carte réseau FDR.  
  
-   Windows Server 2008 R2. Ce système d’exploitation nécessite la carte réseau DDR.  
  
Le serveur doit utiliser les paramètres régionaux en-US pour pouvoir utiliser l’outil de chargement en ligne de commande dwloader. dwloader ne prend pas en charge d’autres paramètres régionaux.  
  
### <a name="networking-requirements-for-windows-server-2012-and-windows-server-2012-r2"></a>Configuration réseau requise pour Windows Server 2012 et Windows Server 2012 R2  
Bien que cela ne soit pas nécessaire pour le chargement, InfiniBand est le type de connexion recommandé pour le chargement des serveurs. Pour de meilleures performances, utilisez Windows Server 2012 ou Windows Server 2012 R2, ainsi que la carte réseau FDR InfiniBand pour connecter le serveur de chargement au réseau de l’appliance InfiniBand.  
  
Pour préparer une connexion Windows Server 2012 ou Windows Server 2012 R2 InfiniBand :  
  
1.  Envisagez de monter en rack le serveur suffisamment près de l’appareil afin de pouvoir le connecter aux commutateurs InfiniBand de l’appliance. Pour plus d’informations sur les technologies Mellanox sur InfiniBand, consultez le livre blanc [Introduction à InfiniBand](https://www.mellanox.com/pdf/whitepapers/IB_Intro_WP_190.pdf).  
  
2.  Achetez une carte réseau Mellanox ConnectX-3 FDR InfiniBand ou double port. Nous vous recommandons d’acheter la carte réseau avec deux ports pour la tolérance de panne pendant la transmission des données. Une carte réseau à deux ports est requise pour la haute disponibilité.  
  
3.  Acheter 2 câbles FDR InfiniBand pour une carte à double port, ou un câble de 1 FDR InfiniBand pour une seule carte de port. Les câbles FDR InfiniBand connectent le serveur de chargement au réseau de l’appliance InfiniBand. La longueur du câble dépend de la distance entre le serveur de chargement et les commutateurs InfiniBand de l’appliance, en fonction de votre environnement.  
  
## <a name="Step3"></a>Étape 3 : connecter le serveur aux réseaux InfiniBand  
Procédez comme suit pour connecter le serveur de chargement au réseau InfiniBand. Si le serveur n’utilise pas le réseau InfiniBand, ignorez cette étape.  
  
1.  Rackez le serveur suffisamment près de l’appareil pour pouvoir le connecter au réseau de l’appliance InfiniBand.  
  
2.  Installez la carte réseau InfiniBand Mellanox ConnectX-3 FDR InfiniBand dans le serveur de chargement.  
  
3.  Utilisez les câbles FDR pour connecter la carte réseau InfiniBand à l’un des deux commutateurs InfiniBand dans le premier rack d’appliances.  
  
4.  Installez et configurez le pilote Windows approprié pour la carte réseau InfiniBand.  
  
    -   Les pilotes InfiniBand pour Windows sont développés par OpenFabrics Alliance, un consortium de l’industrie des fournisseurs InfiniBand.  Le pilote approprié a peut-être été distribué avec votre carte réseau InfiniBand. Si ce n’est pas le cas, le pilote peut être téléchargé à partir de www.openfabrics.org.  
  
5.  Configurez les paramètres InfiniBand et DNS pour les cartes réseau. Pour obtenir des instructions de configuration, consultez [configurer des cartes réseau InfiniBand](configure-infiniband-network-adapters.md).  
  
## <a name="Step4"></a>Étape 4 : installer les outils de chargement  
Les outils clients peuvent être téléchargés à partir du centre de téléchargement Microsoft. 

Pour installer dwloader, exécutez l’installation de dwloader à partir des outils clients.
  
Si vous envisagez d’utiliser Integration Services pour le chargement, vous devez installer Integration Services et les adaptateurs de destination Integration Services. Les adaptateurs sont disponibles dans les outils clients.

<!-- To install the des[Install Integration Services Destination Adapters](install-integration-services-destination-adapters.md). 
--> 
  
## <a name="Step5"></a>Étape 5 : démarrer le chargement  
Vous êtes maintenant prêt à commencer le chargement des données. Pour plus d'informations, consultez les pages suivantes :  
  
1.  [Outil de chargement de ligne de commande dwloader](dwloader.md)  
  
2.  [Vue d’ensemble du chargement](load-overview.md)  
  
## <a name="performance"></a>Performances  
Pour optimiser les performances de chargement sur Windows Server 2012 et versions ultérieures, activez l’initialisation instantanée des fichiers de sorte que lorsque les données sont remplacées, le système d’exploitation ne remplacera pas les données existantes par des zéros. S’il s’agit d’un risque pour la sécurité, car les données antérieures existent toujours sur les disques, veillez à désactiver l’initialisation instantanée des fichiers.  
  
## <a name="Security"></a>Notifications de sécurité  
Étant donné que les données à charger ne sont pas stockées sur l’appliance, votre équipe informatique est responsable de la gestion de tous les aspects de la sécurité de vos données à charger. Par exemple, cela comprend la gestion de la sécurité des données à charger, la sécurité du serveur utilisé pour stocker les chargements et la sécurité de l’infrastructure réseau qui connecte le serveur de chargement à l’appareil SQL Server PDW.  
  
> [!IMPORTANT]  
> Il est particulièrement important de sécuriser chaque serveur de chargement qui utilisera l’outil de chargement de ligne de commande dwloader. Quand dwloader charge des données, il s’authentifie d’abord auprès du nœud de contrôle, puis, après une authentification réussie, il déplace les données du serveur de chargement directement vers les nœuds de calcul sur les canaux de données. La validation du certificat ne se produit pas lors de la main entre chaque serveur de chargement et chaque nœud de calcul. Cela laisse les nœuds de calcul exposés aux attaques potentielles de l’intercepteur sur chaque canal de données lors du chargement. Ces attaques peuvent entraîner une falsification des données et/ou la divulgation d’informations.  
  
Pour réduire les risques de sécurité liés à vos données, nous vous recommandons les éléments suivants :  
  
-   Désigner un compte Windows utilisé uniquement dans le but de charger des données dans PDW. Autorisez ce compte à avoir des autorisations sur l’emplacement de la charge et nulle part ailleurs.  
  
-   Désigner un utilisateur PDW qui dispose des autorisations pour charger des données. Selon vos besoins en matière de sécurité, vous pouvez avoir un utilisateur spécifique par base de données.  
  
-   Les opérations sur le serveur de chargement peuvent accepter un chemin UNC à partir duquel extraire des données de l’extérieur du réseau interne approuvé. Et une personne malveillante sur le réseau, ou avec la possibilité d’influencer la résolution de noms, peut intercepter ou modifier les données envoyées au SQL Server PDW. Cela présente un risque de falsification et de divulgation d’informations. La falsification doit être atténuée en exigeant une signature sur la connexion. Pour réduire ce risque, définissez l’option de stratégie de groupe suivante dans **options de sécurité \** stratégies de sécurité réseau sur le serveur de chargement : **client réseau Microsoft : communications signées numériquement (toujours) : activé**  
  
-   Désactivez l’initialisation instantanée des fichiers sur Windows Server 2012 et versions ultérieures. Il s’agit d’un compromis entre les performances et la sécurité, comme indiqué dans la section performances. Vous devez déterminer ce qui est le mieux en fonction de vos besoins en matière de sécurité.  
  
## <a name="see-also"></a>Voir aussi  
[Vue d’ensemble de la sauvegarde et de la restauration](backup-and-restore-overview.md)  
  
