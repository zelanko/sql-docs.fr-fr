---
title: Écran 1 (pilote ODBC pour SQL Server) de l’Assistant Source de données | Microsoft Docs
ms.custom: ''
ms.date: 09/27/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f13746005f05d84bd8b987fe048baf392e81af3b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47641969"
---
# <a name="data-source-wizard-screen-1"></a>Assistant Source de données, écran 1

Spécifiez le nom et la description de la source de données, et le nom du serveur qui exécute SQL Server et auquel la source des données se connectera. 
    
## <a name="options"></a>Options

### <a name="name"></a>Nom   

Nom de la source de données utilisé par une application ODBC lorsqu'elle demande une connexion à la source de données. Par exemple, "Personnel". Le nom de la source de données est affiché dans la boîte de dialogue Administrateur de la source de données ODBC.

### <a name="description"></a>Description

(Facultatif) Description de la source de données. Par exemple, « date d'embauche, historique de salaire et examen actuel de tous les employés. »

### <a name="select-or-enter-a-server-name"></a>Sélectionnez ou entrez un nom de serveur.

Le nom d’une instance de SQL Server sur votre réseau. Vous devrez spécifier un serveur dans la prochaine zone d'édition.

Dans la plupart des cas, le pilote ODBC peut se connecter suivant l’ordre de protocole par défaut et le nom du serveur fourni dans cette zone. Utilisez le Gestionnaire de configuration SQL Server si vous souhaitez créer un alias pour le serveur ou configurer des bibliothèques réseau de client.

Vous pouvez entrer "(local)" dans la zone Serveur lorsque vous utilisez le même ordinateur que SQL Server. L’utilisateur peut alors se connecter à l’instance locale de SQL Server, même s’il s’agit d’une version de SQL Server qui n’est pas en réseau. Plusieurs instances de SQL Server peuvent s’exécuter sur le même ordinateur. Pour spécifier une instance nommée de SQL Server, le nom de serveur est spécifié ainsi : _NomServeur_\\_NomInstance_.

Pour plus d’informations sur les noms de serveurs de différents types de réseaux, consultez la documentation d’installation de SQL Server dans la Documentation en ligne de SQL Server.

### <a name="finish"></a>Terminer

Si toutes les informations nécessaires pour se connecter à SQL Server sont spécifiées sur cet écran, vous pouvez cliquer sur **Terminer**. Des valeurs par défaut sont utilisées pour tous les attributs spécifiés sur d'autres écrans de l'Assistant.

### <a name="next"></a>Suivant

Pour procéder à l’écran suivant de l’Assistant, cliquez sur **suivant**.

## <a name="next-steps"></a>Étapes suivantes

[Assistant Source de données, écran 2](../../../connect/odbc/windows/dsn-wizard-2.md)
