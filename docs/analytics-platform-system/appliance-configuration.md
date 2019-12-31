---
title: Listes de vérification de la configuration
description: Fournit des listes de vérification pour les tâches requises pour configurer Analytics Platform System pour votre propre environnement. Ces tâches de configuration sont nécessaires pour que vous puissiez utiliser l’appliance.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 80fc899400be167badaae9d617d43a61e0d346b5
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401463"
---
# <a name="appliance-configuration-checklists-for-analytics-platform-system"></a>Listes de vérification de la configuration de l’appliance pour Analytics Platform System
Fournit des listes de vérification pour les tâches requises pour configurer Analytics Platform System pour votre propre environnement. Ces tâches de configuration sont nécessaires pour que vous puissiez utiliser l’appliance.  
  
> [!WARNING]  
> L’utilisation d’Analytics Platform System**Configuration Manager** est la meilleure façon d’effectuer les tâches disponibles dans l’outil, et la seule manière prise en charge.  
  
## <a name="BeforeTasks"></a>Avant de commencer  
  
### <a name="prerequisites"></a>Conditions préalables  
  
1.  L’appliance doit être installée dans le centre de données et sous tension.  
  
2.  Vérifiez que vous disposez des informations suivantes, fournies par votre IHV :  
  
    -   Adresse IP externe du nœud de contrôle PDW (*PDW_region-* CTL01)  
  
    -   Nom de domaine de l’appliance  
  
    -   Nom d’utilisateur et mot de passe de l’administrateur de domaine de l’appliance  
  
3.  Obtenez un certificat approuvé. Vous allez l’importer à une étape ultérieure pour permettre aux clients de se connecter à la **console d’administration** avec des connexions sécurisées. Enregistrez le certificat dans le nœud de contrôle d’un fichier PFX protégé par mot de passe.  
  
4.  Lancez le **Configuration Manager**en procédant comme suit :  
  
    1.  Utilisez **Bureau à distance** pour vous connecter au nœud de contrôle PDW (*PDW_region*-CTL01). (Vous devrez peut-être vous connecter avec l’adresse IP externe pour CTL01.)  
  
    2.  Lancez l' **Configuration Manager** à partir du menu **Démarrer** du nœud de contrôle PDW. Le premier écran de la Configuration Manager affiche la topologie de l’appliance, créée par votre IHV. Il s’agit d’une liste des nœuds matériels reconnus par votre logiciel SQL Server PDW dans le cadre de votre appliance. Vous n’avez pas besoin de modifier les paramètres de l’écran de la topologie de l’appliance.  
  
## <a name="CMTasks"></a>Effectuer des tâches de Configuration Manager  
Le SQL Server PDW**Configuration Manager** (PDWCM) est un outil d’administration d’appliance qui SQL Server PDW les administrateurs système à effectuer des opérations au niveau de l’appliance et à modifier les paramètres de niveau de l’appareil. Par exemple, utilisez PDWCM pour réinitialiser les mots de passe, définissez le fuseau horaire, modifiez les adresses IP, configurez les certificats SSL, activez l’accès à distance via le pare-feu, démarrez ou arrêtez l’appliance, puis définissez l’initialisation instantanée des fichiers.  
  
Utilisez **Configuration Manager** pour effectuer les tâches de configuration suivantes.  
  
|Tâche de configuration|Description|  
|----------------------|---------------|  
|Familiarisez-vous avec les noms de composants physiques|[Composants physiques de l’infrastructure PDW et appliance &#40;Analytics Platform System&#41;](pdw-and-appliance-fabric-physical-components.md)|  
|Lancer SQL Server PDW Configuration Manager|[Lancez le système de plateforme Configuration Manager &#40;Analytics&#41;](launch-the-configuration-manager.md)|  
|Modifier le mot de passe de l’administrateur de domaine|L’appliance dispose d’un Active Directory Domain Services Windows privé qui est utilisé pour authentifier les nœuds au sein de l’appliance.<br /><br />Votre IHV configure l’appliance avec un mot de passe d’administrateur de domaine par défaut. Vous devez le remplacer par un mot de passe sécurisé.<br /><br />Le **Configuration Manager** est la seule méthode prise en charge pour modifier le mot de passe d’administrateur de domaine.<br /><br />Pour plus d’informations, consultez [réinitialisation de mot de passe &#40;Analytics Platform System&#41;](password-reset.md).|  
|Modifier le mot de passe de l’ouverture de session **sa**|SQL Server PDW dispose d’une ouverture de session d’administrateur système nommée **sa**. L’ouverture de session **sa** dispose de tous les privilèges. Il peut accorder, refuser ou révoquer n’importe quelle autorisation. Il peut également voir toutes les vues système.<br /><br />Pour plus d’informations, consultez [réinitialisation de mot de passe &#40;Analytics Platform System&#41;](password-reset.md).|  
|Définir le fuseau horaire de l’appliance|Définissez l’heure (locale ou autre heure souhaitée) pour tous les nœuds de l’appliance.<br /><br />Pour plus d’informations, consultez [Appliance time zone Configuration &#40;Analytics Platform System&#41;](appliance-time-zone-configuration.md).|  
|Spécifier les paramètres réseau en externe pour l’appareil SQL Server PDW|[Configuration réseau de l’appliance &#40;Analytics Platform System&#41;](appliance-network-configuration.md)|  
|Importer un certificat de sécurité pour la console d’administration|Un certificat peut fournir des connexions protocole SSL (SSL) sur HTTPs au [moniteur de l’appliance à l’aide de la console d’administration &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md). Par défaut, la **console d’administration** inclut un certificat auto-signé qui fournit la confidentialité, mais pas l’authentification du serveur. Ce certificat renvoie également une erreur dans Internet Explorer indiquant : « il y a un problème avec le certificat de sécurité de ce site Web » lorsque l’utilisateur se connecte. Bien que cette connexion chiffre les données en vol entre le client et le serveur, la connexion est toujours menacée par les attaquants.<br /><br />SQL Server PDW administrateurs doivent immédiatement acquérir un certificat lié à une autorité de certification approuvée reconnue par les clients, afin de disposer d’une connexion sécurisée et de supprimer l’erreur signalée par Internet Explorer. Cela nécessite un nom de domaine complet qui mappe l’adresse IP virtuelle du nœud de contrôle (recommandé) ou un nom de certificat qui correspond à la valeur que les utilisateurs tapent dans leurs barres d’adresses de navigateur pour accéder à la console d’administration.<br /><br />Utilisez la **Configuration Manager** pour ajouter ou supprimer des certificats approuvés. L’utilisation directe de l’outil de configuration de certificat des`winHttpCertCfg.exe`services http Microsoft Windows () pour gérer les certificats n’est pas prise en charge.<br /><br />Pour plus d’informations, consultez [déploiement de certificats PDW &#40;&#41;système de plateforme d’analyse ](pdw-certificate-provisioning.md).|
|Commutateur de fonctionnalité|Affiche des informations sur les commutateurs de fonctionnalité introduits dans Analytics Platform System AU7. Utilisez cette page pour mettre à jour ou activer/désactiver des fonctionnalités et des paramètres dans Analytics Platform System. La modification des valeurs de commutateur de fonctionnalité nécessite un redémarrage du service.<br /><br />Pour plus d’informations, consultez [commutateur de fonctionnalité PDW &#40;Analytics Platform System&#41;](appliance-feature-switch.md).|
|Activez ou désactivez les règles du pare-feu Windows qui autorisent ou empêchent l’accès à des ports spécifiques sur l’appareil SQL Server PDW.|Votre IHV configure et active les règles de pare-feu nécessaires au bon fonctionnement de l’appliance. Dans la plupart des cas, vous n’activez pas ou ne désactivez pas les règles de pare-feu.<br /><br />Pour plus d’informations, consultez [configuration du pare-feu PDW &#40;Analytics Platform System&#41;](pdw-firewall-configuration.md).|  
|Démarrer et arrêter l’appliance SQL Server PDW|Arrête ou démarre l’appareil SQL Server PDW. Pour plus d’informations, consultez [État des services PDW &#40;Analytics Platform System&#41;](pdw-services-status.md).|  
|Passez en revue les options d’initialisation instantanée de fichier à l’aide de la boîte de dialogue **privilèges**|L’initialisation instantanée de fichiers est une fonctionnalité SQL Server qui permet aux opérations de fichiers de données de s’exécuter plus rapidement. Elle est activée sur SQL Server PDW uniquement si le privilège de SE_MANAGE_VOLUME_NAME a été accordé au compte de service réseau. Elle est désactivée par défaut.<br /><br />Pour plus d’informations, consultez [configuration de l’initialisation de fichiers instantanée &#40;Analytics Platform System&#41;](instant-file-initialization-configuration.md).|  
|Restaurer la base de données Master à partir d’une sauvegarde|Supprime la base de données **Master** active et la remplace par une sauvegarde. Pour plus d’informations, consultez [restaurer la base de données Master &#40;Analytics Platform System&#41;](restore-the-master-database.md).|  
  
## <a name="AddTasks"></a>Effectuer des tâches de configuration supplémentaires  
Après avoir effectué les tâches de **Configuration Manager** , effectuez la liste suivante de tâches de configuration supplémentaires. Certaines de ces tâches sont facultatives.  
  
|Tâche de configuration|Description|  
|----------------------|---------------|  
|Des logiciels antivirus tiers peuvent être installés et configurés sur l’appareil SQL Server PDW pour les nœuds accessibles de l’extérieur.<br /><br />(facultatif)|Pour plus d’informations, consultez [Antivirus Software &#40;Analytics Platform System&#41;](antivirus-software.md).|  
|Le mot de passe pour DSRM peut être modifié.<br /><br />(facultatif)|Pour plus d’informations, consultez [définir le mot de passe d’administrateur pour la connexion aux nœuds AD en mode de restauration des services d’annuaire &#40;DSRM&#41; &#40;Analytics Platform System&#41;](set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode.md).|  
|Configurer l’appliance pour recevoir des mises à jour logicielles<br /><br />(Recommandé)|L’appliance doit être configurée pour recevoir les mises à jour des SQL Server PDW et des logiciels sous-jacents.<br /><br />Pour plus d’informations, consultez [configurer Windows Server Update Services &#40;WSUS&#41; &#40;Analytics Platform System&#41;](configure-windows-server-update-services-wsus.md). Pour plus d’informations sur WSUS, voir [maintenance logicielle &#40;Analytics Platform System&#41;](software-servicing.md).|  
|Configurez la connectivité aux données externes telles que Hadoop ou le stockage d’objets BLOB Azure.<br /><br />(facultatif)|Pour plus d’informations, consultez [configurer la connectivité Polybase à des données externes &#40;Analytics Platform System&#41;](configure-polybase-connectivity-to-external-data.md).|  
|Configurer un logiciel antivirus<br /><br />(facultatif)|Des solutions antivirus tierces peuvent être utilisées pour protéger des nœuds accessibles de l’extérieur, mais elles ne sont pas requises. Suivez les instructions de la.|  
|Configurer des cartes réseau InfiniBand sur les serveurs de sauvegarde et de chargement<br /><br />(facultatif)|Pour configurer les serveurs de sauvegarde et de chargement afin qu’ils se connectent à SQL Server PDW à l’aide du réseau InfiniBand, vous devez configurer les cartes réseau pour permettre au DNS de l’appliance de résoudre la connexion InfiniBand au réseau InfiniBand actuellement actif.|  
|Configurer pour envoyer des données de télémétrie à Microsoft<br /><br />(facultatif)|Pour configurer Analytics Platform System pour envoyer des données de télémétrie à Microsoft, vous devez exécuter un script PowerShell sur le nœud de contrôle. Pour obtenir des instructions spécifiques, consultez [Envoyer des commentaires de télémétrie à Microsoft &#40;SQL Server PDW&#41;](send-telemetry-feedback-to-microsoft-sql-server-pdw.md).|  
  
## <a name="see-also"></a>Voir aussi  
[Logiciel antivirus &#40;Analytics Platform System&#41;](antivirus-software.md)  
[Configurer les cartes réseau InfiniBand &#40;SQL Server PDW&#41;](configure-infiniband-network-adapters.md)  
  
