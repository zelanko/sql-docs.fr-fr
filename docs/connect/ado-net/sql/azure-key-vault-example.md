---
description: Exemple illustrant l’utilisation du fournisseur Azure Key Vault avec Always Encrypted
title: Exemple illustrant l’utilisation du fournisseur Azure Key Vault avec Always Encrypted | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.reviewer: v-kaywon
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: tutorial
author: karinazhou
ms.author: v-jizho2
ms.openlocfilehash: b0f389a822b3fcc37572b34a17cd5780f1091bd4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88438661"
---
# <a name="example-demonstrating-use-of-azure-key-vault-provider-with-always-encrypted"></a>Exemple illustrant l’utilisation du fournisseur Azure Key Vault avec Always Encrypted

[!INCLUDE [sqlserver2019-windows-only](../../../includes/applies-to-version/sqlserver2019-windows-only.md)]

[!INCLUDE [appliesto-netfx-netcore-xxxx-md](../../../includes/appliesto-netfx-netcore-xxxx-md.md)]

Cet exemple illustre l’utilisation du fournisseur Azure Key Vault lors de l’accès à des colonnes chiffrées.

[!code-csharp [AKVProvider Example#1](~/../sqlclient/doc/samples/AzureKeyVaultProviderExample.cs#1)]

## <a name="see-also"></a>Voir aussi

- [Exemple illustrant l’utilisation du fournisseur Azure Key Vault avec Always Encrypted activé avec des Enclaves sécurisées](azure-key-vault-enclave-example.md)
- [Tutoriel : Développer une application .NET en utilisant Always Encrypted avec enclaves sécurisées](tutorial-always-encrypted-enclaves-develop-net-apps.md)
- [Utilisation d’Always Encrypted avec le Fournisseur de données Microsoft .NET pour SQL Server](sqlclient-support-always-encrypted.md)
