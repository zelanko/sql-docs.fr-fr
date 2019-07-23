---
title: Erreurs courantes liées au chiffrement transparent des données avec des clés managées par le client dans Azure Key Vault | Microsoft Docs
description: Résolvez les problèmes de Transparent Data Encryption (TDE) avec une configuration d’Azure Key Vault.
helpviewer_keywords:
- troublshooting, tde akv
- tde akv configuration, troubleshooting
- tde troubleshooting
author: aliceku
ms.prod: sql
ms.technology: security
ms.reviewer: vanto
ms.topic: conceptual
ms.date: 04/26/2019
ms.author: aliceku
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: f67d1ed9bf809baaa4d934947e86d3fd1b7ed0b9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68111532"
---
# <a name="common-errors-for-transparent-data-encryption-with-customer-managed-keys-in-azure-key-vault"></a>Erreurs courantes liées au chiffrement transparent des données avec des clés managées par le client dans Azure Key Vault

[!INCLUDE[appliesto-xx-asdb-asdw-xxx-md.md](../../../includes/appliesto-xx-asdb-asdw-xxx-md.md)]
Cet article décrit les conditions d’utilisation du chiffrement transparent des données (TDE) avec des clés managées par le client dans Azure Key Vault et comment identifier et résoudre les erreurs courantes.

## <a name="requirements"></a>Spécifications

Pour résoudre les problèmes TDE avec un protecteur TDE managé par le client dans Key Vault, vous devez respecter ces exigences :

- L’instance SQL Server logique et le coffre de clés doivent se trouver dans la même région.
- L’identité de l’instance SQL Server logique fournie par Azure Active Directory (Azure AD), AppId dans Azure Key Vault, doit être un locataire dans l’abonnement d’origine. Si le serveur a été déplacé vers un autre abonnement que celui où il a été créé, l’identité du serveur (AppId) doit être recréée.
- Le coffre de clés doit être en cours d’exécution. Pour savoir comment vérifier l’état du coffre de clés, consultez [Azure Resource Health](https://docs.microsoft.com/azure/service-health/resource-health-overview). Pour vous inscrire aux notifications, lisez les informations sur les [groupes d’actions](https://docs.microsoft.com/azure/azure-monitor/platform/action-groups).
- Dans un scénario de géo-reprise d’activité, les deux coffres de clés doivent contenir les mêmes éléments de clé pour un basculement réussi.
- Le serveur logique doit avoir une identité Azure AD (AppId) pour s’authentifier auprès du coffre de clés.
- L’AppId doit avoir accès au coffre de clés et les autorisations Get, Wrap et Unwrap pour les clés sélectionnées en tant que protecteurs TDE.

Pour plus d’informations, consultez [Instructions de configuration de TDE avec Azure Key Vault](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql#guidelines-for-configuring-tde-with-azure-key-vault).

## <a name="common-misconfigurations"></a>Erreurs de configuration courantes

La plupart des problèmes qui se produisent lorsque vous utilisez TDE avec Key Vault sont provoquées par l’une des erreurs de configuration suivantes :

### <a name="the-key-vault-is-unavailable-or-doesnt-exist"></a>Le coffre de clés n’est pas disponible ou n’existe pas

- Le coffre de clés a été supprimé accidentellement.
- Le pare-feu a été configuré pour Azure Key Vault mais n’autorise pas l’accès aux services Microsoft.

### <a name="no-permissions-to-access-the-key-vault-or-the-key-doesnt-exist"></a>Aucune autorisation d’accéder au coffre de clés ou la clé n’existe pas

- La clé a été supprimée accidentellement.
- L’AppId de l’instance SQL Server logique a été supprimé accidentellement.
- L’instance SQL Server logique a été déplacée vers un autre abonnement. Un nouvel AppId doit être créé si le serveur logique est déplacé vers un autre abonnement.
- Les autorisations accordées à l’AppId pour les clés ne sont pas suffisantes (Get, Wrap et Unwrap ne sont pas inclus).
- Les autorisations pour l’AppId de l’instance SQL Server logique ont été révoquées.

## <a name="identify-and-resolve-common-errors"></a>Identifier et résoudre les erreurs courantes

Dans cette section, nous répertorions les étapes de résolution des problèmes pour les erreurs les plus courantes.

### <a name="missing-server-identity"></a>Identité de serveur manquante

**Message d'erreur**

_401 AzureKeyVaultNoServerIdentity - L’identité du serveur n’est pas correctement configurée sur le serveur. Contactez le support._

**Détection**

Utilisez la cmdlet ou commande suivante pour vous assurer qu’une identité a bien été attribuée à l’instance SQL Server logique :

- Azure PowerShell : [Get-AzureRMSqlServer](https://docs.microsoft.com/powershell/module/AzureRM.Sql/Get-AzureRmSqlServer?view=azurermps-6.13.0) 

- Azure CLI : [az-sql-server-show](https://docs.microsoft.com/cli/azure/sql/server?view=azure-cli-latest#az-sql-server-show)

**Atténuation**

Utilisez la cmdlet ou commande suivante pour configurer une identité Azure AD (AppId) pour l’instance SQL Server logique :

- Azure PowerShell : [Set-AzureRmSqlServer](https://docs.microsoft.com/powershell/module/azurerm.sql/set-azurermsqlserver?view=azurermps-6.13.0) avec l’option `-AssignIdentity`.

- Azure CLI : [az sql server update](https://docs.microsoft.com/cli/azure/sql/server?view=azure-cli-latest#az-sql-server-update) avec l’option `--assign_identity`.

Dans le portail Azure, accédez au coffre de clés, puis à **Stratégies d’accès**. Suivez ces étapes : 

 1. Utilisez le bouton **Ajouter** pour ajouter l’AppId du serveur créé à l’étape précédente. 
 1. Attribuez les autorisations de clé suivantes : Get, Wrap et Unwrap 

Pour en savoir plus, consultez [Affecter une identité Azure AD à votre serveur](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql-configure?view=sql-server-2017&viewFallbackFrom=azuresqldb-current#step-1-assign-an-azure-ad-identity-to-your-server).

> [!IMPORTANT]
> Si l’instance SQL Server logique a été transférée vers un nouvel abonnement après la configuration initiale de TDE avec Key Vault, répétez l’étape pour configurer l’identité Azure AD pour créer le nouvel AppId. Ensuite, ajoutez l’AppId dans le coffre de clés et attribuez les autorisations appropriées à la clé. 
>

### <a name="missing-key-vault"></a>Coffre de clés manquant

**Message d'erreur**

_503 AzureKeyVaultConnectionFailed - Impossible d’effectuer l’opération sur le serveur en raison de l’échec des tentatives de connexion à Azure Key Vault._

**Détection**

Pour identifier l’URI de la clé et le coffre de clé :

1. Utilisez la cmdlet ou commande suivante pour obtenir l’URI de la clé d’une instance SQL Server logique spécifique :

    - Azure PowerShell : [Get-AzureRmSqlServerKeyVaultKey](https://docs.microsoft.com/powershell/module/azurerm.sql/get-azurermsqlserverkeyvaultkey?view=azurermps-6.13.0)

    - Azure CLI : [az-sql-server-tde-key-show](https://docs.microsoft.com/cli/azure/sql/server/tde-key?view=azure-cli-latest#az-sql-server-tde-key-show) 

1. Utilisez l’URI de la clé pour identifier le coffre de clés :

    - Azure PowerShell : Vous pouvez inspecter les propriétés de la variable $MyServerKeyVaultKey pour obtenir plus d’informations sur le coffre de clés.

    - Azure CLI : Inspectez le protecteur de chiffrement de serveur retourné pour plus d’informations sur le coffre de clés.

**Atténuation**

Confirmez que le coffre de clés est disponible :

- Vérifiez que le coffre de clés est disponible et que l’instance SQL Server logique y a accès.
- Si le coffre de clés se trouve derrière un pare-feu, assurez-vous que la case permettant aux services Microsoft d’accéder au coffre de clés est cochée.
- Si le coffre de clés a été supprimé accidentellement, vous devez recommencer la configuration depuis le début.


### <a name="missing-key"></a>Clé manquante

**Messages d’erreur**

_404 ServerKeyNotFound - la clé serveur demandée est introuvable sur l’abonnement actuel._ 

_409 ServerKeyDoesNotExists - la clé du serveur n’existe pas._

**Détection**

Pour identifier l’URI de la clé et le coffre de clé :

- Utilisez la cmdlet ou les commandes dans [Coffre de clés manquant](#missing-key-vault) pour identifier l’URI de la clé qui est ajouté à l’instance SQL Server logique. L’exécution des commandes retourne la liste des clés.

**Atténuation**

Confirmez que le protecteur TDE est présent dans Key Vault :

1. Identifiez le coffre de clés et accédez à celui-ci dans le portail Azure.
1. Vérifiez que la clé identifiée par l’URI de la clé est présente.

### <a name="missing-permissions"></a>Autorisations manquantes

**Message d'erreur**

_401 AzureKeyVaultMissingPermissions - le serveur ne dispose pas des autorisations requises pour Azure Key Vault._

**Détection**

Pour identifier l’URI de la clé et le coffre de clés : 

- Utilisez la cmdlet ou les commandes dans [Coffre de clés manquant](#missing-key-vault) pour identifier le coffre de clés utilisé par l’instance SQL Server logique.

**Atténuation**

Vérifiez que l’instance SQL Server logique dispose des autorisations d’accès pour le coffre de clés et des autorisations appropriées pour accéder à la clé :

- Dans le portail Azure, accédez au coffre de clés > **Stratégies d’accès**. Recherchez l’AppId de l’instance SQL Server logique.  
- Si l’AppId est présent, vérifiez qu’il dispose des autorisations de clé suivantes : Get, Wrap et Unwrap.
- Si l’AppId n’est pas présent, ajoutez-le à l’aide du bouton **Ajouter**. 

## <a name="next-steps"></a>Étapes suivantes

- Consultez les [Instructions de configuration de TDE avec Azure Key Vault](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql#guidelines-for-configuring-tde-with-azure-key-vault).
- En savoir plus sur [Azure Resource Health](https://docs.microsoft.com/azure/service-health/resource-health-overview).
- Actualisez vos connaissances sur la façon [d’affecter une identité Azure AD à votre serveur](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql-configure?view=sql-server-2017&viewFallbackFrom=azuresqldb-current#step-1-assign-an-azure-ad-identity-to-your-server).
