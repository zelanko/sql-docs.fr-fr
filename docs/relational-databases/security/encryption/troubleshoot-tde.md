---
title: Erreurs courantes et résolutions avec Transparent Data Encryption (TDE) avec les clés gérées par le client dans Azure Key Vault (AKV) | Microsoft Docs
description: Résolvez les problèmes de Transparent Data Encryption (TDE) avec la configuration d’Azure Key Vault.
helpviewer_keywords:
- troublshooting, tde akv
- tde akv configuration, troubleshooting
- tde troubleshooting
author: aliceku
manager: craigg
ms.prod: sql
ms.technology: security
ms.reviewer: vanto
ms.topic: conceptual
ms.date: 04/26/2019
ms.author: aliceku
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 1366d0a20ed39b466d1a2f6cb3e84f0f30e17f9f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718085"
---
# <a name="common-errors-and-resolutions-with-transparent-data-encryption-tde-with-customer-managed-keys-in-azure-key-vault-akv"></a>Erreurs courantes et résolutions avec Transparent Data Encryption (TDE) avec les clés gérées par le client dans Azure Key Vault (AKV)

[!INCLUDE[appliesto-xx-asdb-asdw-xxx-md.md](../../../includes/appliesto-xx-asdb-asdw-xxx-md.md)]
Cette rubrique aborde les sujets suivants :  
  
- Spécifications  
- Comment identifier et résoudre les erreurs les plus courantes

## <a name="requirements"></a>Spécifications
Pour résoudre les problèmes dans [TDE avec le protecteur TDE géré par le client dans la configuration d’AKV](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql#guidelines-for-configuring-tde-with-azure-key-vault), commencez par confirmer les exigences suivantes :
- Le serveur SQL logique et le coffre de clés doivent se trouver dans la même région.
- L’identité du serveur SQL logique fournie par Azure Active Directory (APPID dans Azure Key Vault) est limitée à un abonné dans l’abonnement d’origine.  Si le serveur a été transféré vers un autre abonnement, l’identité du serveur (APPID) doit être recréée.
- Le coffre de clés doit être opérationnel, consultez [Azure Resource Health](https://docs.microsoft.com/azure/service-health/resource-health-overview) pour vérifier l’état du coffre de clés et [groupes d’actions](https://docs.microsoft.com/azure/azure-monitor/platform/action-groups) pour vous inscrire aux notifications.
- Dans le scénario de géo-reprise d’activité, les deux coffres de clés doivent contenir les mêmes éléments de clé pour un basculement réussi.
- Le serveur logique doit disposer d’une identité Azure Active Directory (AAD) (APPID) afin de s’authentifier auprès du coffre de clés.
- L’APPID doit avoir accès au coffre de clés et les autorisations de type inclure, ne pas inclure et obtenir pour les clés sélectionnées en tant que protecteurs TDE.

La plupart des problèmes rencontrés lors de l’utilisation de TDE avec AKV proviennent d’une des erreurs de configuration suivantes :

### <a name="key-vault-unavailable-or-doesnt-exist"></a>Coffre de clés non disponible ou n’existe pas ?
- Coffre de clés supprimé accidentellement
- Pare-feu configuré pour Azure Key Vault mais n’autorise pas l’accès aux services Microsoft

### <a name="no-permissions-to-access-the-key-vault-or-key-doesnt-exist"></a>Aucune autorisation d’accéder au coffre de clés ou la clé n’existe pas ?
- Clé supprimée accidentellement
- APPID SQL supprimé accidentellement
- SQL a été transféré vers un autre abonnement, ce qui nécessite un nouvel APPID
- Autorisations insuffisantes accordées à APPID pour les clés (inclure, exclure, obtenir)
- Autorisations d’accès à SQL APPID révoquées


Dans la section suivante, nous allons répertorier les étapes de résolution des problèmes pour les erreurs les plus courantes.


## <a name="how-to-identify-and-resolve-the-most-common-errors"></a>Comment identifier et résoudre les erreurs les plus courantes

## <a name="missing-server-identity"></a>Identité de serveur manquante
Message d’erreur : « 401 AzureKeyVaultNoServerIdentity - L’identité du serveur n’est pas correctement configurée sur le serveur. Contactez le support. »

Détection : Utilisez la commande suivante pour vous assurer qu’une identité a bien été attribuée au serveur SQL logique :

- [Azure PowerShell Get-AzureRMSqlServer](https://docs.microsoft.com/powershell/module/AzureRM.Sql/Get-AzureRmSqlServer?view=azurermps-6.13.0) 
- [Azure CLI az-sql-server-show](https://docs.microsoft.com/cli/azure/sql/server?view=azure-cli-latest#az-sql-server-show)

Atténuation des risques : Configurez une identité Azure Active Directory (Azure AD) (APPID) pour le serveur SQL logique

Pour PowerShell : Utilisez la commande Set-AzureRmSqlServer avec option [-AssignIdentity](https://docs.microsoft.com/powershell/module/azurerm.sql/set-azurermsqlserver?view=azurermps-6.13.0) 

Pour l’interface CLI : Utilisez la commande az sql server update avec option [-AssignIdentity](https://docs.microsoft.com/cli/azure/sql/server?view=azure-cli-latest#az-sql-server-update) 

Dans le portail Azure, accédez au coffre de clés et accédez à Stratégies d’accès :  
 - à l’aide du bouton Ajouter un nouveau, ajoutez l’APPID du serveur créé à l’étape précédente. 
 - Attribuez les autorisations de clé suivantes : Get, Wrap et Unwrap 

[En savoir plus](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql-configure?view=sql-server-2017&viewFallbackFrom=azuresqldb-current#step-1-assign-an-azure-ad-identity-to-your-server)

> [!IMPORTANT]
> Si le serveur SQL logique a été transféré vers un nouvel abonnement après la configuration initiale de TDE avec AKV, l’étape pour configurer l’identité AAD doit être répétée pour créer le nouvel APPID.  Le nouvel APPID doit ensuite être ajouté au coffre de clés et les autorisations appropriées doivent être réassignées. 
>

## <a name="missing-key-vault"></a>Coffre de clés manquant
Message d'erreur : « 503 AzureKeyVaultConnectionFailed - Impossible d’effectuer l’opération sur le serveur en raison de l’échec des tentatives de connexion au coffre de clés Azure »

Détection : Comment identifier l’URI de la clé et le coffre de clés 

Étape 1 : Utilisez la commande suivante pour obtenir l’URI de la clé d’un serveur SQL logique donné :

-[Azure PowerShell get-azurermsqlserverkeyvaultkey](https://docs.microsoft.com/powershell/module/azurerm.sql/get-azurermsqlserverkeyvaultkey?view=azurermps-6.13.0)

-[Azure CLI az-sql-server-tde-key-show](https://docs.microsoft.com/cli/azure/sql/server/tde-key?view=azure-cli-latest#az-sql-server-tde-key-show) 

Étape 2 : Utilisez l’URI de clé pour identifier le coffre de clés

PowerShell : Vous pouvez inspecter les propriétés de $MyServerKeyVaultKey pour obtenir plus d’informations sur le coffre de clés

Interface CLI : Inspectez le protecteur de chiffrement de serveur retourné pour plus d’informations sur le coffre de clés

Atténuation des risques : Confirmez que le coffre de clés est disponible
- Vérifiez que le coffre de clés est disponible et que le serveur SQL logique y a accès
- Si le coffre de clés se trouve derrière un pare-feu, assurez-vous que la case permettant aux services Microsoft d’accéder au coffre de clés est cochée
- Si le coffre de clés a été supprimé accidentellement, la configuration doit être refaite à partir du début


## <a name="missing-key"></a>Clé manquante 
Message d'erreur : « 404 ServerKeyNotFound - la clé serveur demandée est introuvable sur l’abonnement actuel. »
« 409 ServerKeyDoesNotExists - la clé du serveur n’existe pas. »

Détection : Comment identifier l’URI de la clé et le coffre de clés
- Identifiez l’URI de clé ajoutée au serveur SQL logique en utilisant les cmdlets de la section Coffre de clés manquant ci-dessus pour retourner la liste de clés.

Atténuation des risques : Confirmez que le protecteur TDE est présent dans AKV
- Identifiez le coffre de clés et y accéder dans le portail Azure
- Vérifiez que la clé identifiée par l’URI de clé est présente

## <a name="missing-permissions"></a>Autorisations manquantes 
Message d'erreur : « 401 AzureKeyVaultMissingPermissions - le serveur ne dispose pas des autorisations requises pour Azure Key Vault. »

Détection : Comment identifier l’URI de la clé et le coffre de clés
- Identifiez le coffre de clés utilisé par le serveur SQL logique en utilisant les cmdlets de la section Coffre de clés manquant ci-dessus.

Atténuation des risques : Vérifiez que le serveur logique SQL dispose des autorisations d’accès pour le coffre de clés et des autorisations appropriées pour accéder à la clé
- Dans le portail Azure, accédez au coffre de clés, accédez à Stratégies d’accès puis localisez l’APPID du serveur SQL :  
  - Si l’APPID n’est pas présent, ajoutez-le à l’aide du bouton Ajouter un nouveau. 
  - Si l’APPID est présent, vérifiez qu’il dispose des autorisations de clé suivantes : Get, Wrap et Unwrap.
