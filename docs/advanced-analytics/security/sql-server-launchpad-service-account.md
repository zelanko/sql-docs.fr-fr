---
title: Configuration de compte de service SQL Server Launchpad - SQL Server Machine Learning Services
description: Comment modifier le compte de service Launchpad de SQL Server utilisé pour l’exécution du script externe sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: ad6377e73633d34b322e5f455f0dd08143c53529
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962334"
---
# <a name="sql-server-launchpad-service-configuration"></a>Configuration du service Launchpad de SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Le [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] est un service qui gère et exécute des scripts externes, similaires à la façon dont le service d’indexation et de requête de recherche en texte intégral lance un hôte distinct pour le traitement des requêtes de recherche en texte intégral.

Pour plus d’informations, consultez les sections de Launchpad dans [architecture d’extensibilité dans SQL Server Machine Learning Services](../../advanced-analytics/concepts/extensibility-framework.md#launchpad) et [vue d’ensemble de la sécurité pour l’infrastructure d’extensibilité dans SQL Server Machine Learning Services](../../advanced-analytics/concepts/security.md#launchpad).

## <a name="account-permissions"></a>Autorisations de compte

Par défaut, SQL Server Launchpad est configuré pour s’exécuter sous **NT Service\MSSQLLaunchpad**, qui est doté de toutes les autorisations nécessaires pour exécuter des scripts externes. Suppression des autorisations de ce compte peut entraîner Launchpad le basculement pour démarrer ou pour accéder à l’instance de SQL Server exécutant des scripts externes.

Si vous modifiez le compte de service, veillez à utiliser le [console de stratégie de sécurité locale](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/how-to-configure-security-policy-settings).

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

1. Ouvrez le [Gestionnaire de configuration de SQL Server](../../relational-databases/sql-server-configuration-manager.md).

2. Sous SQL Server Services, cliquez sur SQL Server Launchpad et sélectionnez **propriétés**.
  + Pour modifier le compte de service, cliquez sur le **ouverture de session** onglet.
  + Pour augmenter le nombre d’utilisateurs, cliquez sur le **avancé** onglet et modifier le **nombre de contextes de sécurité**.

> [!Note]
> Dans les premières versions de SQL Server 2016 R Services, vous pouvez modifier certaines propriétés du service en modifiant le [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] fichier de configuration. Ce fichier est n’est plus utilisé pour la modification des configurations. Gestionnaire de Configuration SQL Server est la bonne approche pour les modifications de configuration du service, telles que le compte de service et le nombre d’utilisateurs.

## <a name="debug-settings"></a>Paramètres de débogage

Quelques propriétés peuvent uniquement être modifiées à l’aide du fichier de configuration de la zone de lancement qui peut-être être utile dans certains cas limités, telles que le débogage. Le fichier de configuration est créé pendant la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le programme d’installation et par défaut est enregistré dans un fichier texte brut dans `<instance path>\binn\rlauncher.config`.

Pour pouvoir apporter des modifications à ce fichier, vous devez être administrateur sur l’ordinateur exécutant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Si vous modifiez le fichier, nous vous recommandons de faire une copie de sauvegarde avant d’enregistrer les modifications.

Le tableau suivant répertorie les paramètres avancés de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], avec les valeurs autorisées.

|**Nom du paramètre**|**Type**|**Description**|
|----|----|----|
|TRAVAIL\_NETTOYAGE\_ON\_QUITTER|Entier |Il s’agit d’un paramètre exclusivement interne - ne modifiez pas cette valeur. </br></br>Spécifie si le dossier de travail temporaire créé pour chaque session de runtime externe doit être nettoyé après que la session est terminée. Ce paramètre est utile pour le débogage. </br></br>Valeurs prises en charge sont **0** (désactivé) ou **1** (activé). </br></br>La valeur par défaut est 1, les fichiers journaux de signification sont supprimés à la sortie.|
|TRACE\_NIVEAU|Entier |Configure le niveau de détail de trace de MSSQLLAUNCHPAD pour le débogage. Cela affecte les fichiers de trace dans le chemin d’accès spécifié par le paramètre LOG_DIRECTORY. </br></br>Valeurs prises en charge : **1** (erreur), **2** (Performance), **3** (avertissement), **4** (informations). </br></br>La valeur par défaut est 1, ce qui signifie seulement les erreurs de sortie.|

Tous les paramètres prennent la forme d’une paire clé-valeur, chaque paramètre figurant sur une ligne distincte. Par exemple, pour modifier le niveau de trace, vous ajoutez la ligne `Default: TRACE_LEVEL=4`.

<a name="bkmk_EnforcePolicy"></a>

## <a name="enforcing-password-policy"></a>Application de la stratégie de mot de passe

Si votre organisation a mis en place une stratégie exigeant le changement périodique des mots de passe, vous devrez peut-être forcer le service Launchpad à regénérer les mots de passe chiffrés qu’il gère pour ses comptes de travail.

Pour activer ce paramètre et forcer l’actualisation des mots de passe, ouvrez le volet **Propriétés** du service Launchpad dans le Gestionnaire de configuration SQL Server, cliquez sur **Avancé**, puis affectez à **Réinitialiser le mot de passe des utilisateurs externes** la valeur **Oui**. Quand vous appliquez ce changement, les mots de passe sont immédiatement regénérés pour tous les comptes d’utilisateurs. Pour exécuter un script externe après cette modification, vous devez redémarrer le service Launchpad, moment auquel il lira les mots de passe qui vient d’être générés.

Pour réinitialiser les mots de passe à intervalles réguliers, vous pouvez définir cet indicateur manuellement ou utiliser un script.

## <a name="next-steps"></a>Étapes suivantes

+ [Infrastructure d’extensibilité](../concepts/extensibility-framework.md)
+ [Vue d’ensemble de la sécurité](../concepts/security.md)
