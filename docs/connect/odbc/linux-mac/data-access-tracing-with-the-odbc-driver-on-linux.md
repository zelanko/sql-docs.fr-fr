---
title: Traçage de l’accès aux données avec le pilote ODBC sur Linux et macOS| Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data access tracing
- tracing
ms.assetid: 3149173a-588e-47a0-9f50-edb8e9adf5e8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1fa39cd11f70a661de5c284e56f2ccc0f7a5777f
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "68008822"
---
# <a name="data-access-tracing-with-the-odbc-driver-on-linux-and-macos"></a>Traçage de l’accès aux données avec le pilote ODBC sur Linux et macOS

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Le gestionnaire de pilotes unixODBC sur macOS et Linux prend en charge le traçage de l’entrée et de la sortie d’appel d’API ODBC pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].

Pour suivre le comportement ODBC de votre application, modifiez la section `[ODBC]` du fichier `odbcinst.ini` pour définir les valeurs `Trace=Yes` et `TraceFile` sur le chemin d’accès du fichier qui doit contenir la sortie de suivi ; par exemple :

```ini
[ODBC]
Trace=Yes
TraceFile=/home/myappuser/odbctrace.log
```

(Vous pouvez également utiliser `/dev/stdout` ou tout autre nom d’appareil pour envoyer une sortie de suivi au lieu d’un fichier persistant.) Avec les paramètres ci-dessus, chaque fois qu’une application charge le gestionnaire de pilotes unixODBC, elle enregistre tous les appels API ODBC qu’elle a effectués dans le fichier de sortie.

Une fois que vous avez fini de tracer votre application, supprimez `Trace=Yes` du fichier `odbcinst.ini` pour éviter de dégrader les performances de traçage et garantir la suppression des fichiers de trace inutiles.

Le traçage s’applique à toutes les applications qui utilisent le pilote dans `odbcinst.ini`. Pour ne pas tracer toutes les applications (par exemple, pour éviter la divulgation d’informations sensibles par utilisateur), vous pouvez tracer une instance d’application individuelle en lui fournissant l’emplacement d’un fichier `odbcinst.ini` privé, à l’aide de la variable d’environnement `ODBCSYSINI`. Par exemple :

```bash
$ ODBCSYSINI=/home/myappuser myapp
```

Dans ce cas, vous pouvez ajouter `Trace=Yes` à la section `[ODBC Driver 13 for SQL Server]` de `/home/myappuser/odbcinst.ini`.

## <a name="determining-which-odbcini-file-the-driver-is-using"></a>Détermination du fichier odbc.ini utilisé par le pilote

Les pilotes ODBC Linux et macOS ne savent pas quel fichier `odbc.ini` est en cours d’utilisation ni le chemin d’accès au fichier `odbc.ini`. Des informations sur le fichier `odbc.ini` en cours d’utilisation sont néanmoins disponibles à partir des outils unixODBC `odbc_config` et `odbcinst`, et dans la documentation du gestionnaire de pilotes unixODBC.

Par exemple, la commande suivante imprime (parmi d’autres informations) l’emplacement des fichiers `odbc.ini` système et utilisateur qui contiennent, respectivement, les noms de source de données système et utilisateur :

```
$ odbcinst -j
unixODBC 2.3.1
DRIVERS............: /etc/odbcinst.ini
SYSTEM DATA SOURCES: /etc/odbc.ini
FILE DATA SOURCES..: /etc/ODBCDataSources
USER DATA SOURCES..: /home/odbcuser/.odbc.ini`
SQLULEN Size.......: 8
SQLLEN Size........: 8
SQLSETPOSIROW Size.: 8
```

La [documentation unixODBC](http://www.unixodbc.org/doc/UserManual/) explique les différences entre les noms DSN utilisateur et système. En résumé :

- DSN utilisateur : noms de sources de notification (DNS) disponibles uniquement pour un utilisateur spécifique. Les utilisateurs peuvent se connecter, ajouter, modifier et supprimer leurs propres DSN utilisateur. Les DSN utilisateur sont stockés dans un fichier situé dans le répertoire d'origine de l'utilisateur ou dans un sous-répertoire de celui-ci.

- DSN système : ces DSN sont disponibles pour tous les utilisateurs du système qui se connectent, mais ils peuvent uniquement être ajoutés, modifiés et supprimés par un administrateur système. Si un utilisateur dispose d’un DSN utilisateur portant le même nom qu’un DSN système, le DSN utilisateur sera utilisé lors des connexions de cet utilisateur.

## <a name="see-also"></a>Voir aussi

- [Instructions de programmation](../../../connect/odbc/linux-mac/programming-guidelines.md)
