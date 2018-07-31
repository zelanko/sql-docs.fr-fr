---
title: Traçage de l’accès aux données avec le pilote ODBC sur Linux et macOS| Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data access tracing
- tracing
ms.assetid: 3149173a-588e-47a0-9f50-edb8e9adf5e8
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 64a04e7c448161c22ca9a671e5fdbe706829bced
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "37982184"
---
# <a name="data-access-tracing-with-the-odbc-driver-on-linux-and-macos"></a>Traçage de l’accès aux données avec le pilote ODBC sur Linux et macOS
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Le Gestionnaire de pilotes unixODBC sur macOS et Linux prend en charge le traçage de l’entrée des appels API ODBC et de sortie du pilote ODBC pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].

Pour suivre le comportement de votre application ODBC, vous devez modifier le `odbcinst.ini` du fichier `[ODBC]` section pour définir les valeurs `Trace=Yes` et `TraceFile` pour le chemin d’accès du fichier qui doit contenir la trace de sortie ; par exemple :

```  
Trace=Yes
TraceFile=/home/myappuser/odbctrace.log
```  

(Vous pouvez également utiliser `/dev/stdout` ou tout autre nom d’appareil pour envoyer la trace de sortie il au lieu de dans un fichier persistant.) Avec les paramètres ci-dessus, chaque fois qu’une application charge le Gestionnaire de pilotes unixODBC il enregistrera tous les appels d’API ODBC qui elle est effectuée dans le fichier de sortie.

Une fois que vous avez terminé le traçage de votre application, supprimez `Trace=Yes` à partir de la `odbcinst.ini` pour éviter la baisse des performances du suivi de fichier et assurez-vous que tous les fichiers inutiles de trace sont supprimés.
  
Le traçage s’applique à toutes les applications qui utilisent le pilote dans `odbcinst.ini`. Pour ne pas tracer toutes les applications (par exemple, pour éviter la divulgation d’informations sensibles par utilisateur), vous pouvez tracer une instance d’application individuelle en lui fournissant l’emplacement d’un fichier `odbcinst.ini` privé, à l’aide de la variable d’environnement `ODBCSYSINI`. Exemple :  
  
```  
$ ODBCSYSINI=/home/myappuser myapp
```  
  
Dans ce cas, vous pouvez ajouter `Trace=Yes` à la `[ODBC Driver 13 for SQL Server]` section de `/home/myappuser/odbcinst.ini`.

## <a name="determining-which-odbcini-file-the-driver-is-using"></a>Détermination du fichier odbc.ini utilisé par le pilote

Les pilotes ODBC de Linux et macOS ne savez pas quelle `odbc.ini` est utilisée, ou le chemin d’accès à la `odbc.ini` fichier. Toutefois, les informations sur les `odbc.ini` fichier est en cours est disponible à partir des outils unixODBC `odbc_config` et `odbcinst`et à partir de la documentation du Gestionnaire de pilotes unixODBC.  
  
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

Le [documentation unixODBC](http://www.unixodbc.org/doc/UserManual/) explique les différences entre l’utilisateur et les sources de données système. En résumé :  

- Sources de données utilisateur---il s’agit des sources de données qui sont disponibles uniquement pour un utilisateur spécifique. Les utilisateurs peuvent se connecter à l’aide, ajouter, modifier et supprimer leur propres sources de données utilisateur. Sources de données utilisateur sont stockés dans un fichier dans le répertoire de base utilisateur ou un sous-répertoire.
  
- Système DSN---ces sources de données sont disponibles pour chaque utilisateur sur le système de se connecter à leur utilisation, mais peuvent uniquement être ajoutés, modifiées et supprimés par un administrateur système. Si un utilisateur a un DSN utilisateur portant le même nom en tant que système DSN, le DSN utilisateur sera utilisé lors de connexions par cet utilisateur.

## <a name="see-also"></a> Voir aussi
[Instructions de programmation](../../../connect/odbc/linux-mac/programming-guidelines.md)
