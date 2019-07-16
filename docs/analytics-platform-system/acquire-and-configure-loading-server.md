---
title: Obtenir et configurer un serveur de chargement - Parallel Data Warehouse | Microsoft Docs
description: Cet article décrit comment obtenir et configurer un serveur de chargement comme un système de Windows non-appliance pour l’envoi des chargements de données à Parallel Data Warehouse (PDW).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: d753237841695786de3d368bebf9a606875ea634
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961611"
---
# <a name="acquire-and-configure-a-loading-server-for-parallel-data-warehouse"></a>Obtenir et configurer un serveur de chargement pour Parallel Data Warehouse
Cet article décrit comment obtenir et configurer un serveur de chargement comme un système de Windows non-appliance pour l’envoi des chargements de données à Parallel Data Warehouse (PDW).  
  
## <a name="Basics"></a>Principes de base  
Le chargement du serveur :  
  
-   Ne devra pas être un serveur unique. Vous pouvez charger en même temps que plusieurs serveurs de chargement.  
  
-   Est fourni et géré par votre propre équipe informatique. Vous disposez peut-être déjà un serveur ou les serveurs qui peuvent être utilisées pour le chargement des données dans PDW.  
  
-   Se trouve dans votre propre rack non-appliance et ne peut pas être placé dans l’appliance Analytique Platform System.  
  
-   Est connecté à l’appliance via le réseau InfiniBand de l’Appliance ou via une connexion Ethernet. Pour des performances, nous vous recommandons d’utiliser InfiniBand.  
  
-   Se trouve dans votre propre domaine client, pas le domaine de l’appliance. Il n’existe aucune relation d’approbation entre le domaine de votre client et le domaine de l’appliance.  
  
## <a name="Step1"></a>Étape 1 : Déterminer la capacité requise  
Le système de chargement peut être conçu comme un ou plusieurs serveurs de chargement qui effectuent des chargements simultanés. Chaque serveur de chargement ne devra pas être dédié uniquement au chargement, tant qu’il gère les exigences de performances et de stockage de votre charge de travail.  
  
La configuration système requise pour un serveur de chargement dépend presque entièrement votre propre charge de travail. Utilisez le [le chargement des feuille de planification de capacité de serveur](loading-server-capacity-planning-worksheet.md) pour aider à déterminer vos besoins en capacité.  
  
## <a name="Step2"></a>Étape 2 : Acquérir le Sserveur  
Maintenant que vous comprenez mieux vos besoins en capacité, vous pouvez planifier les serveurs et les composants réseau dont vous aurez besoin d’acheter ou mettre en service. Incorporer la liste suivante des exigences de votre plan d’achat, puis acheter votre serveur ou configurer un serveur existant.  
  
### <a name="R"></a>Configuration logicielle requise  
Systèmes d’exploitation pris en charge :  
  
-   Windows Server 2012 ou Windows Server 2012 R2. Ces systèmes d’exploitation nécessitent l’adaptateur de réseau FDR.  
  
-   Windows Server 2008 R2. Ce système d’exploitation nécessite la carte réseau DDR.  
  
Le serveur doit utiliser les paramètres régionaux EN-US pour pouvoir utiliser l’outil de ligne de commande du chargement de dwloader. dwloader ne prend pas en charge les autres paramètres régionaux.  
  
### <a name="networking-requirements-for-windows-server-2012-and-windows-server-2012-r2"></a>Configuration réseau requise pour Windows Server 2012 et Windows Server 2012 R2  
Bien que ne pas obligatoires pour le chargement, InfiniBand est le type de connexion recommandée pour le chargement des serveurs. Pour de meilleures performances, utilisez Windows Server 2012 ou Windows Server 2012 R2 et la carte réseau InfiniBand FDR pour connecter le serveur de chargement au réseau InfiniBand appliance.  
  
Pour préparer une connexion de Windows Server 2012 ou Windows Server 2012 R2 InfiniBand :  
  
1.  Envisagez de monter en rack de serveur suffisamment proches pour l’appliance afin que vous pouvez vous connecter à l’appliance InfiniBand bascule. Pour plus d’informations à partir de Technologies Mellanox InfiniBand, consultez le livre blanc, [présentation InfiniBand](https://www.mellanox.com/pdf/whitepapers/IB_Intro_WP_190.pdf).  
  
2.  Acheter une carte Mellanox ConnectX-3 FDR InfiniBand port simple ou double. Nous vous recommandons d’acheter la carte réseau avec deux ports pour une tolérance de panne pendant la transmission de données. Une carte réseau de deux port est requise pour la haute disponibilité.  
  
3.  Acheter 2 câbles FDR InfiniBand pour une carte de port double ou 1 câble FDR InfiniBand pour une carte de port unique. Les câbles FDR InfiniBand se connectera le chargement du serveur au réseau InfiniBand appliance. La longueur du câble dépend de la distance entre le serveur de chargement et les commutateurs InfiniBand du matériel, en fonction de votre environnement.  
  
## <a name="Step3"></a> Étape 3 : Connectez le serveur aux réseaux InfiniBand  
Suivez ces étapes pour connecter le serveur de chargement pour le réseau InfiniBand. Si le serveur n’utilise pas le réseau InfiniBand, ignorez cette étape.  
  
1.  Le serveur de rack suffisamment à l’appliance afin que vous pouvez vous connecter au réseau InfiniBand appliance.  
  
2.  Installez l’adaptateur de réseau InfiniBand Mellanox ConnectX-3 FDR InfiniBand sur le serveur de chargement.  
  
3.  Utilisez les câbles FDR pour connecter la carte réseau InfiniBand à un des deux commutateurs InfiniBand dans le rack appliance premier.  
  
4.  Installez et configurez le pilote Windows approprié pour la carte réseau InfiniBand.  
  
    -   Les pilotes InfiniBand pour Windows sont développés par OpenFabrics Alliance, un consortium d’entreprises de fournisseurs de InfiniBand.  Le pilote correct peut ont été distribué avec votre carte de réseau InfiniBand. Si ce n’est pas le cas, le pilote peut être téléchargé à partir de www.openfabrics.org.  
  
5.  Configurez les paramètres DNS et InfiniBand pour les cartes réseau. Pour obtenir des instructions de configuration, consultez [cartes réseau InfiniBand configurer](configure-infiniband-network-adapters.md).  
  
## <a name="Step4"></a>Étape 4 : Installer les outils de chargement  
Les outils clients sont disponibles en téléchargement à partir du Microsoft Download Center. 

Pour installer dwloader, exécutez l’installation de dwloader dans les outils clients.
  
Si vous envisagez d’utiliser les Services d’intégration pour le chargement, vous devrez installer Integration Services et les adaptateurs de destination Integration Services. Les adaptateurs sont disponibles dans les outils clients.

<!-- To install the des[Install Integration Services Destination Adapters](install-integration-services-destination-adapters.md). 
--> 
  
## <a name="Step5"></a>Étape 5 : Démarrer le chargement  
Vous êtes maintenant prêt à commencer le chargement des données. Pour plus d'informations, consultez :  
  
1.  [Outil de chargement de ligne de commande de dwloader](dwloader.md)  
  
2.  [Vue d’ensemble de la charge](load-overview.md)  
  
## <a name="performance"></a>Performances  
Pour meilleures performances sur Windows Server 2012 et au-delà de chargement, activer l’initialisation instantanée de fichier afin que lorsque les données sont remplacées, le système d’exploitation ne remplacera pas les données existantes avec des zéros. S’il s’agit d’un risque de sécurité, car les données précédentes existent toujours sur les disques, veillez à désactiver l’initialisation instantanée des fichiers.  
  
## <a name="Security"></a>Avis de sécurité  
Dans la mesure où les données à charger ne sont pas stockées sur l’appliance, votre équipe informatique est chargé de gérer tous les aspects de la sécurité de vos données à charger. Par exemple, cela inclut la gestion de la sécurité des données à charger, de la sécurité du serveur utilisé pour stocker des charges et de la sécurité de l’infrastructure réseau qui connecte le serveur de chargement à l’appliance SQL Server PDW.  
  
> [!IMPORTANT]  
> Il est particulièrement important de sécuriser chaque serveur de chargement qui utilisera l’outil de ligne de commande du chargement de dwloader. Lorsque dwloader charge des données, il s’authentifie d’abord avec le nœud de contrôle, et puis après une authentification réussie il déplace les données à partir du serveur de chargement directement aux nœuds de calcul via les canaux de données. Validation du certificat n’a pas lieu pendant les tremblements entre chaque serveur de chargement et de chaque nœud de calcul. Cela laisse les nœuds de calcul exposés à des attaques potentielles man-in-the-middle sur chaque canal de données lors du chargement. Ces attaques peuvent entraîner des données falsifiées et/ou la divulgation d’informations.  
  
Pour réduire les risques de sécurité avec vos données, nous vous conseillons des éléments suivants :  
  
-   Désigner un compte Windows qui est utilisé aux seules fins de chargement de données dans PDW. Autoriser ce compte dispose des autorisations pour l’emplacement de la charge et nulle part ailleurs.  
  
-   Désigner un utilisateur PDW qui dispose des autorisations pour charger des données. Selon vos besoins de sécurité, vous pourriez avoir un utilisateur spécifique par base de données.  
  
-   Opérations sur le serveur de chargement peuvent accepter un chemin d’accès UNC à partir de laquelle pour extraire les données à partir de l’extérieur du réseau interne approuvé. Et une personne malveillante sur le réseau ou avec la possibilité pour influencer la résolution de noms peut intercepter ou de modifier les données envoyées à l’ordinateur SQL Server PDW. Cela pose un risque de divulgation d’informations et de falsification. Falsification doit être atténuée par exiger la signature sur la connexion. Pour atténuer ce risque, définissez l’option de stratégie de groupe suivante **Security Settings\Local Policies\Security Options** sur le serveur de chargement :  **Client réseau Microsoft : Communications signées numériquement (toujours) : Activé**  
  
-   Désactivez l’initialisation instantanée des fichiers sur Windows Server 2012 et au-delà. Il s’agit d’un compromis entre performances et la sécurité, comme indiqué dans la section performances. Vous devez décider ce qui convient le mieux en fonction de vos exigences de sécurité.  
  
## <a name="see-also"></a>Voir aussi  
[Vue d’ensemble de sauvegarde et de restauration](backup-and-restore-overview.md)  
  
