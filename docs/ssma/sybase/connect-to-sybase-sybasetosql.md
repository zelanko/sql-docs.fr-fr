---
title: Se connecter à Sybase (SybaseToSQL) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 524f95ef-10bd-497c-84ca-c06a0ae794fb
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: e1302d7e57d7ef2559d107039648e813e1292efa
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34778397"
---
# <a name="connect-to-sybase-sybasetosql"></a>Se connecter à Sybase (SybaseToSQL)
Utilisez le **se connecter à Sybase** boîte de dialogue se connecter à l’instance de Sybase Adaptive Server Enterprise (ASE) que vous souhaitez migrer.  
  
Pour accéder à cette boîte de dialogue, dans le **fichier** menu, sélectionnez **se connecter à Sybase**. Si vous êtes déjà connecté, la commande est **se reconnecter pour Sybase**.  
  
## <a name="options"></a>Options  
**Fournisseur**  
Sélectionnez un du fournisseur installé sur l’ordinateur pour la connexion au serveur de Sybase.  
  
**Mode**  
Sélectionnez les deux modes de connexion standard ou avancé. En mode standard, vous entrez ou sélectionnez des valeurs pour le nom du serveur, le port, le nom d’utilisateur et le mot de passe. En mode avancé, vous fournissez une chaîne de connexion.  
  
**Nom du serveur**  
Entrez ou sélectionnez le nom ou l’adresse IP du serveur adaptative. Le nom du serveur par défaut est le même que le nom de l’ordinateur. Il s’agit d’une option de mode standard.  
  
**Port du serveur**  
Si vous utilisez un port non défini par défaut pour les connexions à ASE, entrez le numéro de port. Le numéro de port par défaut est 5000. Il s’agit d’une option de mode standard.  
  
**Nom d'utilisateur**  
Entrez le nom d’utilisateur qui est utilisé pour se connecter à ASE. Il s’agit d’une option de mode standard.  
  
**Mot de passe**  
Entrez le mot de passe correspondant au nom d'utilisateur indiqué. Il s’agit d’une option de mode standard.  
  
**Chaîne de connexion**  
Entrez la chaîne de connexion complète pour la connexion à ASE.  
  
Chaînes de connexion sont constitués de paires nom / valeur de paramètre. Les noms des paramètres varient en fonction du fournisseur utilisé.  
  
**Paramètres de connexion pour différents fournisseurs sont les suivantes :**  
  
1.  Paramètres de connexion de **fournisseur OLE DB**  
  
    |Paramètre|Paramètre de Sybase 12,5|Paramètre de Sybase 15|  
    |-----------|-------------------------|-----------------------|  
    |Nom du serveur|Nom du serveur|Serveur|  
    |d’|Adresse de Port du serveur|d’|  
    |Nom d’utilisateur|ID d'utilisateur|ID d'utilisateur|  
    |Mot de passe|Mot de passe|Mot de passe|  
    |Fournisseur|Fournisseur|Fournisseur|  
  
    Pour Sybase ASE 12,5, un exemple de chaîne de connexion est la suivante :  
  
    `Server Name=sybserver;User ID=MyUserID;Password=MyP@$$word;Provider=Sybase.ASEOLEDBProvider;`  
  
    Pour Sybase ASE 15, un exemple de chaîne de connexion est la suivante :  
  
    `Server=sybserver;User ID=MyUserID;Password=MyP@$$word;Provider=ASEOLEDB;Port=5000;`  
  
2.  Paramètres de connexion de **fournisseur ODBC**  
  
    |Paramètre|Paramètre de Sybase 12,5/15|  
    |-----------|-----------------------------|  
    |Nom du pilote|Pilote|  
    |Nom du serveur|Serveur|  
    |Nom d'utilisateur|UID|  
    |Mot de passe|Mot de passe|  
    |Numéro de port|d’|  
  
    Pour Sybase ASE 12,5 ou 15, un exemple de chaîne de connexion est la suivante :  
  
    `driver=Adaptive Server Enterprise;Server=sybserver;uid=MyUserID;pwd=MyP@$$word;Port=5000;`  
  
3.  Paramètres de connexion de **fournisseur ADO.NET**  
  
    |Paramètre|Paramètre de Sybase 12,5/15|  
    |-----------|-----------------------------|  
    |Nom du serveur|Serveur|  
    |Nom d'utilisateur|UID|  
    |Mot de passe|Mot de passe|  
    |Numéro de port|d’|  
  
    Un exemple de chaîne de connexion pour le fournisseur ADO.NET est comme suit :  
  
    `Server=sybserver;Port=5000;uid=MyUserID;pwd=MyP@$$word;`  
  
Pour plus d’informations, consultez la documentation de ASE.  
  
Il s’agit d’une option de mode avancé.  
  
