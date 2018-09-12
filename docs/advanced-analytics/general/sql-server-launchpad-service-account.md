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
ms.openlocfilehash: 0afdb02c578de92bc91c5f47e973148136ebd919
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43892860"
---
# <a name="sql-server-launchpad-service-configuration"></a>Configuration du service Launchpad de SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Distinct [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] service est créé pour l’instance du moteur de base de données à laquelle vous avez ajouté SQL Server machine learning (R ou Python) integration.

## <a name="service-account-configuration"></a>Configuration de compte de service

Par défaut, SQL Server Launchpad est configuré pour s’exécuter sous **NT Service\MSSQLLaunchpad**, qui est doté de toutes les autorisations nécessaires pour exécuter des scripts externes. Suppression des autorisations de ce compte peut entraîner Launchpad le basculement pour démarrer ou pour accéder à l’instance de SQL Server exécutant des scripts externes.

Autorisation requise pour ce compte sont répertoriés ci-dessous. Si vous modifiez le compte de service, veillez à utiliser le **stratégie de sécurité locale** application pour inclure ces autorisations :

+ Changer les quotas de mémoire d'un processus (SeIncreaseQuotaPrivilege)
+ Outrepasser le contrôle de parcours (SeChangeNotifyPrivilege)
+ Ouvrir une session en tant que service (SeServiceLogonRight)
+ Remplacer un jeton de niveau processus (SeAssignPrimaryTokenPrivilege)

Pour plus d’informations sur les autorisations requises pour exécuter les services SQL Server, consultez [Configurer les comptes de service Windows et les autorisations](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

<a name="bkmk_ChangingConfig"></a> 

## <a name="configuration-properties"></a>Propriétés de configuration

1. Ouvrez le [Gestionnaire de configuration SQL Server](../../relational-databases/sql-server-configuration-manager.md). 

2. Cliquez sur le Launchpad de SQL Server et sélectionnez **propriétés**.

    + Pour modifier le compte de service, cliquez sur le **ouverture de session** onglet.

    + Pour augmenter le nombre d’utilisateurs, cliquez sur le **avancé** onglet.

> [!Note]
> Dans les premières versions de SQL Server 2016 R Services, vous pouvez modifier certaines propriétés du service en modifiant le [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] fichier de configuration. Ce fichier est n’est plus utilisé pour la modification des configurations. Gestionnaire de Configuration SQL Server est la bonne approche pour les modifications de configuration du service, telles que le compte de service et le nombre d’utilisateurs.

#### <a name="debug-settings"></a>Paramètres de débogage

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
