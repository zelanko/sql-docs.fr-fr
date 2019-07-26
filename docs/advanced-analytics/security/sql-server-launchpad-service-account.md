---
title: Configuration du compte de service SQL Server Launchpad
description: Comment modifier le compte de service SQL Server Launchpad utilisé pour l’exécution de scripts externes sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 5d01004fb54c0410acc372c5c66930f33bbd8856
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469997"
---
# <a name="sql-server-launchpad-service-configuration"></a>Configuration du service SQL Server Launchpad
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Le [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] est un service qui gère et exécute des scripts externes, de la même façon que le service d’indexation et de recherche en texte intégral lance un hôte distinct pour le traitement des requêtes de texte intégral.

Pour plus d’informations, consultez les sections Launchpad dans [architecture d’extensibilité dans SQL Server machine learning services](../../advanced-analytics/concepts/extensibility-framework.md#launchpad) et [vue d’ensemble de la sécurité pour l’infrastructure d’extensibilité dans SQL Server machine learning services](../../advanced-analytics/concepts/security.md#launchpad).

## <a name="account-permissions"></a>Autorisations de compte

Par défaut, SQL Server Launchpad est configuré pour s’exécuter sous **NT Service\MSSQLLaunchpad**, qui est approvisionné avec toutes les autorisations nécessaires pour exécuter des scripts externes. La suppression des autorisations de ce compte peut entraîner l’échec du démarrage de Launchpad ou l’accès à l’instance SQL Server dans laquelle les scripts externes doivent être exécutés.

Si vous modifiez le compte de service, veillez à utiliser la [console Stratégie de sécurité locale](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/how-to-configure-security-policy-settings).

Les autorisations requises pour ce compte sont répertoriées dans le tableau suivant.

| Paramètre de stratégie de groupe | Nom de la constante |
|----------------------|---------------|
| [Ajuster les quotas de mémoire pour un processus](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/adjust-memory-quotas-for-a-process) | SeIncreaseQuotaPrivilege | 
| [Ignorer la vérification de parcours](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/bypass-traverse-checking) | SeChangeNotifyPrivilege | 
| [Ouvrir une session en tant que service](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/log-on-as-a-service) | SeServiceLogonRight | 
| [Remplacer un jeton au niveau du processus](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/replace-a-process-level-token) | SeAssignPrimaryTokenPrivilege | 

Pour plus d’informations sur les autorisations requises pour exécuter les services SQL Server, consultez [Configurer les comptes de service Windows et les autorisations](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

<a name="bkmk_ChangingConfig"></a> 

## <a name="configuration-properties"></a>Propriétés de configuration

En règle générale, il n’y a aucune raison de modifier la configuration du service. Les propriétés qui peuvent être modifiées incluent le compte de service, le nombre de processus externes (20 par défaut) ou la stratégie de réinitialisation de mot de passe pour les comptes de travail.

1. Ouvrez le [Gestionnaire de configuration de SQL Server](../../relational-databases/sql-server-configuration-manager.md).

2. Sous services de SQL Server, cliquez avec le bouton droit sur SQL Server Launchpad et sélectionnez **Propriétés**.
  + Pour modifier le compte de service, cliquez sur l’onglet **ouvrir une session** .
  + Pour augmenter le nombre d’utilisateurs, cliquez sur l’onglet **avancé** et modifiez le nombre de contextes de **sécurité**.

> [!Note]
> Dans les premières versions de SQL Server 2016 R services, vous pouviez modifier certaines propriétés du service en modifiant le [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] fichier de configuration. Ce fichier n’est plus utilisé pour modifier les configurations. Gestionnaire de configuration SQL Server est la bonne approche pour les modifications apportées à la configuration de service, telles que le compte de service et le nombre d’utilisateurs.

## <a name="debug-settings"></a>Paramètres de débogage

Certaines propriétés ne peuvent être modifiées qu’à l’aide du fichier de configuration de Launchpad, ce qui peut être utile dans certains cas limités, tels que le débogage. Le fichier de configuration est créé lors [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de l’installation et est enregistré par défaut en tant que fichier `<instance path>\binn\rlauncher.config`texte brut dans.

Pour pouvoir apporter des modifications à ce fichier, vous devez être administrateur sur l’ordinateur exécutant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Si vous modifiez le fichier, nous vous recommandons de faire une copie de sauvegarde avant d’enregistrer les modifications.

Le tableau suivant répertorie les paramètres avancés [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]pour, avec les valeurs autorisées.

|**Nom du paramètre**|**Type**|**Description**|
|----|----|----|
|NETTOYAGE\_\_DU TRAVAIL À LA SORTIE\_|Entier |Il s’agit d’un paramètre interne uniquement: ne modifiez pas cette valeur. </br></br>Spécifie si le dossier de travail temporaire créé pour chaque session de Runtime externe doit être nettoyé une fois la session terminée. Ce paramètre est utile pour le débogage. </br></br>Les valeurs prises en charge sont **0** (désactivé) ou **1** (activé). </br></br>La valeur par défaut est 1, ce qui signifie que les fichiers journaux sont supprimés à la sortie.|
|NIVEAU\_DE SUIVI|Entier |Configure le niveau de détail de la trace de MSSQLLAUNCHPAD à des fins de débogage. Cela affecte les fichiers de trace dans le chemin d’accès spécifié par le paramètre LOG_DIRECTORY. </br></br>Valeurs prises en charge : **1** (erreur), **2** (performances), **3** (avertissement), **4** (informations). </br></br>La valeur par défaut est 1, ce qui signifie uniquement les erreurs de sortie.|

Tous les paramètres prennent la forme d’une paire clé-valeur, chaque paramètre figurant sur une ligne distincte. Par exemple, pour modifier le niveau de suivi, vous devez ajouter la `Default: TRACE_LEVEL=4`ligne.

<a name="bkmk_EnforcePolicy"></a>

## <a name="enforcing-password-policy"></a>Application de la stratégie de mot de passe

Si votre organisation a mis en place une stratégie exigeant le changement périodique des mots de passe, vous devrez peut-être forcer le service Launchpad à regénérer les mots de passe chiffrés qu’il gère pour ses comptes de travail.

Pour activer ce paramètre et forcer l’actualisation des mots de passe, ouvrez le volet **Propriétés** du service Launchpad dans le Gestionnaire de configuration SQL Server, cliquez sur **Avancé**, puis affectez à **Réinitialiser le mot de passe des utilisateurs externes** la valeur **Oui**. Quand vous appliquez ce changement, les mots de passe sont immédiatement regénérés pour tous les comptes d’utilisateurs. Pour exécuter un script externe après cette modification, vous devez redémarrer le service Launchpad, à l’heure où il lira les mots de passe nouvellement générés.

Pour réinitialiser les mots de passe à intervalles réguliers, vous pouvez définir cet indicateur manuellement ou utiliser un script.

## <a name="next-steps"></a>Étapes suivantes

+ [Infrastructure d’extensibilité](../concepts/extensibility-framework.md)
+ [Vue d’ensemble de la sécurité](../concepts/security.md)
