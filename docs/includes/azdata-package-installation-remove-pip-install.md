---
author: MikeRayMSFT
ms.prod: sql
ms.topic: include
ms.date: 01/07/2020
ms.author: mikeray
ms.openlocfilehash: 0c15fb58bb076724402ab72f81e58ce46c8b7b1e
ms.sourcegitcommit: ae474d21db4f724523e419622ce79f611e956a22
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92257394"
---
### <a name="pythonpip-installation"></a>Installation de Python/Pip

Vous pouvez installer [!INCLUDE [azure-data-cli-azdata](../includes/azure-data-cli-azdata.md)]sur Linux avec yum, apt ou zypper ou sur MacOS avec les gestionnaires de packages d’installation Homebrew. Avant que ces gestionnaires de package soient disponibles, l’installation nécessitait Python et PIP.

>[!IMPORTANT]
>Avant de continuer, vous devez supprimer toutes les installations de `azdata` qui ont été installées dans le système Python global. Les nouveaux programmes d’installation ou les packages natifs ajoutent `azdata` à votre chemin d’accès et il est impossible de savoir lequel est le premier.
Si une `azdata` existante est installée sur le système Python global, supprimez-la avant de continuer.

Pour afficher votre installation actuelle, exécutez la commande suivante :

```bash
$ pip list --format columns
```

Si `azdata` est installé par PIP, il retourne le package et la version. Par exemple :

```
 Package             Version
------------------- ----------
azdata-cli          15.0.X
azdata-cli-app      15.0.X
azdata-cli-cluster  15.0.X
azdata-cli-core     15.0.X
azdata-cli-hdfs     15.0.X
azdata-cli-notebook 15.0.X
azdata-cli-profile  15.0.X
azdata-cli-spark    15.0.X
azdata-cli-sql      15.0.X
```

L’exemple suivant supprime une installation PIP de `azdata`.

```bash
$ pip freeze | grep azdata-* | xargs pip uninstall -y
```

Après avoir vérifié que vous avez supprimé une installation de `azdata` qui a été installée avec PIP, procédez à l’installation.