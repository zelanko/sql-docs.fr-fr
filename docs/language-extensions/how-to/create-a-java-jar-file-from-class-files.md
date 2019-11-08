---
title: Créer un fichier jar Java à partir de fichiers class
titleSuffix: SQL Server Language Extensions
description: Découvrir comment créer un fichier jar Java à partir de fichiers class
author: dphansen
ms.author: davidph
ms.date: 07/25/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4cec311a28f9d5119b5a0aeb696597e8b34ba25a
ms.sourcegitcommit: a154b3050b6e1993f8c3165ff5011ff5fbd30a7e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "73588773"
---
# <a name="create-a-java-jar-file-from-class-files"></a>Créer un fichier jar Java à partir de fichiers class
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Quand vous utilisez les [extensions de langage SQL Server](../language-extensions-overview.md), et que vous exécutez du code Java, nous vous recommandons de packager vos fichiers class dans un fichier jar.

## <a name="create-a-jar-file"></a>Créer un fichier jar

Pour créer un fichier jar à partir de fichiers class, accédez au dossier contenant votre fichier class, puis exécutez la commande suivante :

```cmd
jar -cf <MyJar.jar> *.class
```

Vérifiez que le chemin de `jar.exe` fait partie de la variable de chemin système. Vous pouvez également spécifier le chemin complet du fichier jar, qui se trouve sous `/bin`, dans le dossier du kit JDK. Par exemple :

```cmd
C:\Users\MyUser\Desktop\jdk1.8.0_201\bin\jar -cf <MyJar.jar> *.class
```

## <a name="next-steps"></a>Étapes suivantes

+ [Guide pratique pour appeler Java dans SQL Server](../how-to/call-java-from-sql.md)