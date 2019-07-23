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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68008822"
---
# <a name="data-access-tracing-with-the-odbc-driver-on-linux-and-macos"></a>Traçage de l’accès aux données avec le pilote ODBC sur Linux et macOS

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Le gestionnaire de pilotes unixODBC sur macOS et Linux prend en charge le traçage de l’entrée d’appel d’API ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]et la sortie du pilote ODBC pour.

Pour suivre le comportement ODBC de votre application, modifiez `odbcinst.ini` la section `[ODBC]` du fichier pour définir les `Trace=Yes` valeurs `TraceFile` et le chemin d’accès du fichier qui doit contenir la sortie de suivi, par exemple:

```ini
[ODBC]
Trace=Yes
TraceFile=/home/myappuser/odbctrace.log
```

(Vous pouvez également utiliser `/dev/stdout` ou tout autre nom de périphérique pour envoyer la sortie de trace à la place de dans un fichier persistant.) Avec les paramètres ci-dessus, chaque fois qu’une application charge le gestionnaire de pilotes unixODBC, elle enregistre tous les appels d’API ODBC qu’elle a effectués dans le fichier de sortie.

Une fois que vous avez fini de tracer `Trace=Yes` votre application `odbcinst.ini` , supprimez du fichier afin d’éviter une altération des performances du suivi et assurez-vous que tous les fichiers de trace inutiles sont supprimés.

Le traçage s’applique à toutes les applications qui utilisent le pilote dans `odbcinst.ini`. Pour ne pas tracer toutes les applications (par exemple, pour éviter la divulgation d’informations sensibles par utilisateur), vous pouvez tracer une instance d’application individuelle en lui fournissant l’emplacement d’un fichier `odbcinst.ini` privé, à l’aide de la variable d’environnement `ODBCSYSINI`. Par exemple :

```bash
$ ODBCSYSINI=/home/myappuser myapp
```

Dans ce cas, vous pouvez ajouter `Trace=Yes` à la `[ODBC Driver 13 for SQL Server]` section de `/home/myappuser/odbcinst.ini`.

## <a name="determining-which-odbcini-file-the-driver-is-using"></a>Détermination du fichier odbc.ini utilisé par le pilote

Les pilotes ODBC Linux et MacOS ne savent pas lequel `odbc.ini` est en cours d’utilisation ou le chemin `odbc.ini` d’accès au fichier. Toutefois, les informations sur `odbc.ini` le fichier en cours d’utilisation sont disponibles à partir `odbc_config` des `odbcinst`outils unixODBC et et de la documentation du gestionnaire de pilotes unixodbc.

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

La [documentation unixodbc](http://www.unixodbc.org/doc/UserManual/) explique les différences entre les DSN utilisateur et système. En Résumé:

- Les DSN utilisateur---ce sont des noms de sources de notification qui sont disponibles uniquement pour un utilisateur spécifique. Les utilisateurs peuvent se connecter à l’aide de, ajouter, modifier et supprimer leurs propres DSN utilisateur. Les noms de sources de fichiers utilisateur sont stockés dans un fichier dans le répertoire de démarrage de l’utilisateur ou dans un sous-répertoire de celui-ci.

- Les noms de sources de session système---ces DSN sont disponibles pour tous les utilisateurs du système qui se connectent à leur utilisation, mais ils peuvent uniquement être ajoutés, modifiés et supprimés par un administrateur système. Si un utilisateur possède un nom de source de nom d’utilisateur avec le même nom qu’un DSN système, le DSN utilisateur est utilisé sur les connexions de cet utilisateur.

## <a name="see-also"></a>Voir aussi

- [Instructions de programmation](../../../connect/odbc/linux-mac/programming-guidelines.md)
