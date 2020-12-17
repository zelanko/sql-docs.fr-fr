---
title: Propriétés de Alias (onglet Alias)
description: Utilisez l’onglet Alias de la boîte de dialogue Propriétés pour configurer un alias afin de pouvoir utiliser un autre nom lors de la connexion à une instance de SQL Server.
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: 2d1498e2-129c-4ce7-88e5-408e4037243c
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/14/2017
monikerRange: '>=sql-server-2016'
ms.openlocfilehash: 65558dcdc06b42f3f475fae1b0041909bdff8967
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97481710"
---
# <a name="ltaliasgt-properties-alias-tab"></a>Propriétés de &lt;Alias&gt; (onglet Alias)

[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]

Un alias est un nom de remplacement permettant d'établir une connexion. L'alias encapsule les éléments requis d'une chaîne de connexion, puis les expose sous un nom choisi par l'utilisateur. Utilisez la page **Alias** de la boîte de dialogue **Propriétés de \<**Alias name**>** pour afficher ou spécifier les éléments de chaîne de connexion d’un Alias.

## <a name="options"></a>Options

**Nom de l'alias**

Nom (alias) à utiliser pour faire référence à cette connexion.  

**Nom du canal** / **Numéro de port**  

Éléments supplémentaires de la chaîne de connexion. Le nom de cette zone varie en fonction du protocole sélectionné. Consultez les rubriques ci-après pour obtenir des exemples.  

**Protocole**

Protocole utilisé pour la connexion.

**Serveur**

Nom de l’instance [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers laquelle la connexion est établie.  

## <a name="see-also"></a>Voir aussi

- [Création d'une chaîne de connexion valide à l'aide du protocole de mémoire partagée](../../tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)
- [Création d’une chaîne de connexion valide à l’aide du protocole TCP/IP](../../tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)
- [Création d’une chaîne de connexion valide avec des canaux nommés](/previous-versions/sql/sql-server-2016/ms189307(v=sql.130))