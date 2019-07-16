---
title: Listes de vérification de configuration - Analytique Platform System | Microsoft Docs
description: Fournit des listes de contrôle pour les tâches requises pour configurer le système de plateforme d’Analytique pour votre propre environnement. Ces tâches de configuration sont nécessaires avant de pouvoir utiliser l’appliance.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 9977ac8ea73e37afef85a46d6794ea5136357b44
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961594"
---
# <a name="appliance-configuration-checklists-for-analytics-platform-system"></a>Listes de contrôle de configuration pour l’Analytique Platform System appliance
Fournit des listes de contrôle pour les tâches requises pour configurer le système de plateforme d’Analytique pour votre propre environnement. Ces tâches de configuration sont nécessaires avant de pouvoir utiliser l’appliance.  
  
> [!WARNING]  
> À l’aide d’Analytique Platform System**Configuration Manager** est le meilleur moyen, et la seule manière, pour effectuer les tâches disponibles dans l’outil.  
  
## <a name="BeforeTasks"></a>Avant de commencer  
  
### <a name="prerequisites"></a>Prérequis  
  
1.  L’appliance doit être installée dans le centre de données et sous tension.  
  
2.  Vérifiez que vous avez les informations suivantes, qui sont fournies par votre fabricant de matériel :  
  
    -   Adresse IP externe pour le nœud de contrôle de PDW (*PDW_region -* CTL01)  
  
    -   Nom de domaine d’application  
  
    -   Nom d’utilisateur et mot de passe pour l’administrateur de domaine d’application  
  
3.  Obtenir un certificat approuvé. Vous importerez ce dans une étape ultérieure pour autoriser les clients à se connecter à la **Console d’administration** avec des connexions sécurisées. Enregistrer le certificat sur le nœud de contrôle dans le fichier PFX protégé par mot de passe.  
  
4.  Lancer le **Configuration Manager**, en procédant comme suit :  
  
    1.  Utilisez **Bureau à distance** pour se connecter au nœud de contrôle de PDW (*PDW_region*-CTL01). (Vous devrez peut-être vous connecter avec l’adresse IP externe pour CTL01).  
  
    2.  Lancer le **Configuration Manager** à partir de la **Démarrer** menu du nœud de contrôle de PDW. Le premier écran de Configuration Manager affiche la topologie de l’appliance, qui a été créée par votre fabricant de matériel. C’est une liste des nœuds de matériel reconnus par votre logiciel de SQL Server PDW comme faisant partie de votre appliance. Vous ne devez pas modifier les paramètres sur l’écran de la topologie d’appliances.  
  
## <a name="CMTasks"></a>Effectuer des tâches de Configuration Manager  
Le SQL Server PDW**Configuration Manager** (PDWCM) est un outil d’administration d’appliance les administrateurs système SQL Server PDW utilisent pour effectuer des opérations au niveau de l’appliance et pour modifier les paramètres au niveau de l’appliance. Par exemple, utiliser PDWCM pour réinitialiser les mots de passe, définir le fuseau horaire, modifier les adresses IP, configurer des certificats SSL, activer l’accès à distance via le pare-feu, démarrer ou arrêter l’appliance et définissez l’initialisation instantanée des fichiers.  
  
Utilisez **Configuration Manager** pour effectuer les tâches de configuration suivantes.  
  
|Tâche de configuration|Description|  
|----------------------|---------------|  
|Vous familiariser avec les noms des composants physiques|[Composants physiques de PDW et Appliance Fabric &#40;Analytique Platform System&#41;](pdw-and-appliance-fabric-physical-components.md)|  
|Lancez le Gestionnaire de Configuration SQL Server PDW|[Lancez le Gestionnaire de Configuration &#40;Analytique Platform System&#41;](launch-the-configuration-manager.md)|  
|Modification du mot de passe administrateur|L’appliance a un privée Windows Active Directory Domain Services qui est utilisé pour authentifier des nœuds au sein de l’appliance.<br /><br />Votre fabricant de matériel configurer l’appliance avec un mot de passe administrateur de domaine par défaut. Cette opération doit être remplacé par un mot de passe sécurisé.<br /><br />Le **Configuration Manager** est le seul pris en charge permettent de modifier le mot de passe administrateur.<br /><br />Pour plus d’informations, consultez [mot de passe réinitialisé &#40;Analytique Platform System&#41;](password-reset.md).|  
|Modifier le mot de passe pour le **sa** ouverture de session|SQL Server PDW a une ouverture de session administrateur système nommé **sa**. Le **sa** ouverture de session possède tous les privilèges. Il peut accorder, refuser ou révoquer n’importe quelle autorisation. Il peut également voir toutes les vues système.<br /><br />Pour plus d’informations, consultez [mot de passe réinitialisé &#40;Analytique Platform System&#41;](password-reset.md).|  
|Définir le fuseau horaire de matériel|Définir le temps (local ou autres souhaité) pour tous les nœuds d’appliance.<br /><br />Pour plus d’informations, consultez [Configuration fuseau horaire de l’Appliance &#40;Analytique Platform System&#41;](appliance-time-zone-configuration.md).|  
|Spécifiez les paramètres de réseau externe pour l’appliance SQL Server PDW|[Configuration des appliances réseau &#40;Analytique Platform System&#41;](appliance-network-configuration.md)|  
|Importer un certificat de sécurité de la Console d’administration|Un certificat peut fournir des connexions de couche SSL (Secure Sockets) via le protocole HTTPS pour le [surveiller l’Appliance à l’aide de la Console d’administration &#40;Analytique Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md). Par défaut, le **Console d’administration** inclut un certificat auto-signé qui fournit la confidentialité, mais pas l’authentification du serveur. Ce certificat retourne également une erreur dans Internet Explorer indiquant : « Il existe un problème avec le certificat de sécurité de ce site Web » lorsque l’utilisateur se connecte. Bien que cette connexion chiffre les données en transit entre le client et le serveur, la connexion est toujours exposé à des personnes malveillantes.<br /><br />Les administrateurs SQL Server PDW doivent immédiatement acquérir un certificat lié à une autorité de certification approuvée reconnu par les clients, afin de disposer d’une connexion sécurisée et de supprimer l’erreur qui signale d’Internet Explorer. Cela nécessite un nom de domaine complet qui mappe l’adresse IP virtuelle du nœud de contrôle (recommandé) ou un nom de certificat qui correspond à la valeur que les utilisateurs tapent dans leurs adresses du navigateur barres doivent accéder à la Console d’administration.<br /><br />Utilisez le **Configuration Manager** pour ajouter ou supprimer des certificats de confiance. Directement à l’aide de l’outil de Configuration de certificat Microsoft Windows HTTP Services (`winHttpCertCfg.exe`) pour gérer les certificats non pris en charge.<br /><br />Pour plus d’informations, consultez [provisionnement du certificat PWD &#40;Analytique Platform System&#41;](pdw-certificate-provisioning.md).|
|Commutateur de fonctionnalité|Affiche des informations sur les commutateurs de fonctionnalité ont été introduites dans AU7 de système de plateforme Analytique. Utilisez cette page pour mettre à jour ou activer/désactiver les fonctionnalités et les paramètres d’Analytique Platform System. Modification des valeurs de commutateur de fonctionnalité nécessite un redémarrage du service.<br /><br />Pour plus d’informations, consultez [commutateur de fonctionnalité PDW &#40;Analytique Platform System&#41;](appliance-feature-switch.md).|
|Activer ou désactiver des règles de pare-feu de Windows qui autorisent ou empêchent l’accès à des ports spécifiques sur l’appliance SQL Server PDW.|Votre fabricant de matériel sera configurez et activez les règles de pare-feu qui sont nécessaires pour l’application fonctionne correctement. Dans la plupart des cas ne pas activer ou désactiver des règles de pare-feu.<br /><br />Pour plus d’informations, consultez [Configuration du pare-feu PDW &#40;Analytique Platform System&#41;](pdw-firewall-configuration.md).|  
|Démarrer et arrêter l’appliance SQL Server PDW|Arrête ou démarre l’appliance SQL Server PDW. Pour plus d’informations, consultez [l’état des Services PDW &#40;Analytique Platform System&#41;](pdw-services-status.md).|  
|Examiner les options d’initialisation instantanée des fichiers à l’aide de la **des privilèges** boîte de dialogue|Initialisation instantanée des fichiers est une fonctionnalité de SQL Server qui autorise les opérations de fichier de données exécuter plus rapidement. Il est activé sur SQL Server PDW uniquement si le compte Service réseau dispose du privilège SE_MANAGE_VOLUME_NAME. Il est désactivé par défaut.<br /><br />Pour plus d’informations, consultez [Configuration de l’initialisation de fichier instantanée &#40;Analytique Platform System&#41;](instant-file-initialization-configuration.md).|  
|Restaurer la base de données master à partir d’une sauvegarde|Supprime l’actuel **master** de base de données et le remplace par une sauvegarde. Pour plus d’informations, consultez [restaurer la base de données Master &#40;Analytique Platform System&#41;](restore-the-master-database.md).|  
  
## <a name="AddTasks"></a>Effectuer des tâches de Configuration supplémentaires  
Après avoir effectué la **Configuration Manager** effectuer des tâches, la liste suivante des tâches de configuration supplémentaires. Certaines de ces tâches sont facultatives.  
  
|Tâche de configuration|Description|  
|----------------------|---------------|  
|Les logiciels antivirus tiers peuvent être installé et configuré sur l’appliance SQL Server PDW pour exposés extérieurement des nœuds.<br /><br />(facultatif)|Pour plus d’informations, consultez [d’un logiciel Antivirus &#40;Analytique Platform System&#41;](antivirus-software.md).|  
|Le mot de passe DSRM peut être modifié.<br /><br />(facultatif)|Pour plus d’informations, consultez [définir un mot de passe administrateur pour vous connecter à des nœuds AD dans le Mode de restauration des Services d’annuaire &#40;DSRM&#41; &#40;Analytique Platform System&#41;](set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode.md).|  
|Configurer l’appliance pour recevoir des mises à jour logicielles<br /><br />(Recommandé)|L’appliance doit être configuré pour recevoir des mises à jour le SQL Server PDW et le logiciel sous-jacent.<br /><br />Pour plus d’informations, consultez [configurer Windows Server Update Services &#40;WSUS&#41; &#40;Analytique Platform System&#41;](configure-windows-server-update-services-wsus.md). Pour plus d’informations sur WSUS, consultez [maintenance logicielle &#40;Analytique Platform System&#41;](software-servicing.md).|  
|Configurer la connectivité à des données externes telles que Hadoop ou Azure blob storage.<br /><br />(facultatif)|Pour plus d’informations, consultez [configurer la connectivité PolyBase pour données externes &#40;Analytique Platform System&#41;](configure-polybase-connectivity-to-external-data.md).|  
|Configurer les logiciels Antivirus<br /><br />(facultatif)|Solutions antivirus tiers peut être utilisé pour protéger les nœuds exposés en externe, mais n’est pas obligatoire. Suivez les instructions de.|  
|Configurer les cartes réseau InfiniBand sur la sauvegarde et de chargement des serveurs<br /><br />(facultatif)|Pour configurer la sauvegarde et chargement des serveurs pour vous connecter à SQL Server PDW en utilisant le réseau InfiniBand, vous devez configurer les cartes réseau pour autoriser la solution DNS pour résoudre la connexion InfiniBand sur le réseau InfiniBand actuellement actif.|  
|Configurer pour envoyer des données de télémétrie à Microsoft<br /><br />(facultatif)|Pour configurer le système de plateforme d’Analytique pour envoyer des données de télémétrie à Microsoft, vous devez exécuter un script PowerShell sur le nœud de contrôle. Pour obtenir des instructions spécifiques, consultez [envoyer des commentaires des données de télémétrie à Microsoft &#40;SQL Server PDW&#41;](send-telemetry-feedback-to-microsoft-sql-server-pdw.md).|  
  
## <a name="see-also"></a>Voir aussi  
[Un logiciel antivirus &#40;Analytique Platform System&#41;](antivirus-software.md)  
[Configurer les cartes réseau InfiniBand &#40;SQL Server PDW&#41;](configure-infiniband-network-adapters.md)  
  
