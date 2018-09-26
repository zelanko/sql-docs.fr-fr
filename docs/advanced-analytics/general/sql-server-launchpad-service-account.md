---
title: Configuration de compte de service SQL Server Launchpad | Microsoft Docs
description: Comment modifier le compte de service Launchpad de SQL Server utilisé pour l’exécution du script externe sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/05/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 76087367c1ba24894989038fb6fc22427d8be77b
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2018
ms.locfileid: "46712722"
---
# <a name="sql-server-launchpad-service-configuration"></a>Configuration du service Launchpad de SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Distinct [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] service est créé pour chaque instance du moteur de base de données à laquelle vous avez ajouté SQL Server machine learning (R ou Python) integration.

## <a name="account-permissions"></a>Autorisations de compte

Par défaut, SQL Server Launchpad est configuré pour s’exécuter sous **NT Service\MSSQLLaunchpad**, qui est doté de toutes les autorisations nécessaires pour exécuter des scripts externes. Suppression des autorisations de ce compte peut entraîner Launchpad le basculement pour démarrer ou pour accéder à l’instance de SQL Server exécutant des scripts externes.

Si vous modifiez le compte de service, veillez à utiliser le **stratégie de sécurité locale** application (**toutes les applications** > **les outils d’administration Windows**  >  **Stratégie de sécurité locale**).

Autorisations requises pour ce compte sont répertoriées dans le tableau suivant.

| Paramètre de stratégie de groupe | Nom de constante |
|----------------------|---------------|
| [Ajuster les quotas de mémoire pour un processus](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/adjust-memory-quotas-for-a-process) | SeIncreaseQuotaPrivilege | 
| [Contourner la vérification de parcours](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/bypass-traverse-checking) | SeChangeNotifyPrivilege | 
| [Ouvrez une session en tant que service](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/log-on-as-a-service) | SeServiceLogonRight | 
| [Remplacer un jeton de niveau processus](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/replace-a-process-level-token) | SeAssignPrimaryTokenPrivilege | 

Pour plus d’informations sur les autorisations requises pour exécuter les services SQL Server, consultez [Configurer les comptes de service Windows et les autorisations](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

<a name="bkmk_ChangingConfig"></a> 

## <a name="configuration-properties"></a>Propriétés de configuration

En règle générale, il n’existe aucune raison de modifier la configuration du service. Les propriétés qui peut être changées incluent le compte de service, le nombre de processus externes (20 par défaut), ou le mot de passe réinitialisé la stratégie pour les comptes de travail.

1. Ouvrez le [Gestionnaire de configuration SQL Server](../../relational-databases/sql-server-configuration-manager.md). 

  + Sur la page de démarrage, entrez **MMC** pour ouvrir la Console de gestion Microsoft.
  + Sur **fichier** > **ajouter/supprimer un composant logiciel enfichable**, déplacer **Gestionnaire de Configuration SQL Server** de disponible pour les composants logiciels enfichables sélectionnés.

2. Dans SQL Server Configuration Manager sous Services de SQL Server, SQL Server Launchpad d’avec le bouton droit et sélectionnez **propriétés**.

    + Pour modifier le compte de service, cliquez sur le **ouverture de session** onglet.

    + Pour augmenter le nombre d’utilisateurs, cliquez sur le **avancé** onglet.

> [!Note]
> Dans les premières versions de SQL Server 2016 R Services, vous pouvez modifier certaines propriétés du service en modifiant le [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] fichier de configuration. Ce fichier est n’est plus utilisé pour la modification des configurations. Gestionnaire de Configuration SQL Server est la bonne approche pour les modifications de configuration du service, telles que le compte de service et le nombre d’utilisateurs.

## <a name="debug-settings"></a>Paramètres de débogage

Quelques propriétés peuvent uniquement être modifiées à l’aide du fichier de configuration de la zone de lancement qui peut-être être utile dans certains cas limités, telles que le débogage. Le fichier de configuration est créé au cours de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le programme d’installation et par défaut est enregistré comme un fichier texte brut à l’emplacement suivant : `<instance path>\binn\rlauncher.config`

Pour pouvoir apporter des modifications à ce fichier, vous devez être administrateur sur l’ordinateur exécutant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Si vous modifiez le fichier, nous vous recommandons de faire une copie de sauvegarde avant d’enregistrer les modifications.

Le tableau suivant répertorie les paramètres avancés de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], avec les valeurs autorisées. 

|**Nom du paramètre**|**Type**|**Description**|
|----|----|----|
|TRAVAIL\_NETTOYAGE\_ON\_QUITTER|Entier |Il s’agit d’un paramètre exclusivement interne : ne modifiez pas cette valeur. </br></br>Spécifie si le dossier de travail temporaire créé pour chaque session de runtime externe doit être nettoyé après que la session est terminée. Ce paramètre est utile pour le débogage. </br></br>Valeurs prises en charge sont **0** (désactivé) ou **1** (activé). </br></br>La valeur par défaut est 1, les fichiers journaux de signification sont supprimés à la sortie.|
|TRACE\_NIVEAU|Entier |Configure le niveau de détail de trace de MSSQLLAUNCHPAD pour le débogage. Cela affecte les fichiers de trace dans le chemin d’accès spécifié par le paramètre LOG_DIRECTORY. </br></br>Valeurs prises en charge sont : **1** (erreur), **2** (Performance), **3** (avertissement), **4** (informations). </br></br>La valeur par défaut est 1, ce qui signifie seulement les avertissements de sortie.|

Tous les paramètres prennent la forme d’une paire clé-valeur, chaque paramètre figurant sur une ligne distincte. Par exemple, pour modifier le niveau de trace, vous ajoutez la ligne `Default: TRACE_LEVEL=4`.

## <a name="see-also"></a>Voir aussi

[Infrastructure d’extensibilité](../concepts/extensibility-framework.md)
