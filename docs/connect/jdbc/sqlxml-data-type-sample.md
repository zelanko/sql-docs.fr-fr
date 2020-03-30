---
title: Exemple de type de données SQLXML | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8f2ff25b-71fd-46d7-b6de-d656095d2aad
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f0cc8e3e48024e6d5af789919173454d0ee05e56
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "69027651"
---
# <a name="sqlxml-data-type-sample"></a>exemple de type de données SQLXML

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Cet exemple d’application du [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] montre comment stocker des données XML dans une base de données relationnelle, récupérer des données XML à partir d’une base de données et analyser des données XML avec le type de données Java **SQLXML**.

Les exemples de code de cette section utilisent un analyseur SAX (Simple API for XML). La norme SAX est une norme développée de manière publique pour l'analyse de documents XML en fonction des événements. Elle fournit également une interface de programmation d'applications pour l'utilisation des données XML. Notez que les applications peuvent également utiliser d'autres analyseurs XML, par exemple DOM (Document Object Model), StAX (Streaming API for XML), etc.

DOM (Document Object Model) fournit une représentation par programme des documents, fragments, nœuds ou éléments node-set XML. Elle fournit également une interface de programmation d'applications pour l'utilisation des données XML. De même, StAX (Streaming API for XML) est une API Java pour l'analyse par extraction du code XML.

> [!IMPORTANT]  
> Pour pouvoir utiliser l'API de l'analyseur SAX, vous devez importer l'implémentation SAX standard à partir du package javax.xml.

Le fichier de code de cet exemple, SqlXmlDataType.java, se trouve à l’emplacement suivant :

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\datatypes
```

## <a name="requirements"></a>Spécifications

Pour exécuter cet exemple d'application, vous devez définir l'instruction classpath de façon à inclure le fichier sqljdbc4.jar. Si l'instruction classpath n'a pas d'entrée pour sqljdbc4.jar, l'exemple d'application lève l'exception « Classe introuvable ». Pour plus d’informations sur la façon de définir l’instruction classpath, consultez [à l’aide du pilote JDBC](../../connect/jdbc/using-the-jdbc-driver.md).

L’accès à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] est par ailleurs nécessaire pour pouvoir exécuter cet exemple d’application.

## <a name="example"></a>Exemple

Dans l’exemple suivant, le code établit une connexion à la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)], puis appelle la méthode createSampleTables.

La méthode createSampleTables supprime les tables de test TestTable1 et TestTable2, si elles existent. Elle insère ensuite deux lignes dans TestTable1.

En outre, l'exemple de code ajoute les trois méthodes décrites ci-après et une classe supplémentaire dont le nom est ExampleContentHandler.

La classe ExampleContentHandler implémente un gestionnaire de contenu personnalisé qui définit les méthodes pour les événements de l'analyseur.

La méthode showGetters montre comment analyser les données de l’objet SQLXML avec l’analyseur SAX, ContentHandler et XMLReader. En premier lieu, l'exemple de code crée une instance d'un gestionnaire de contenu personnalisé dont le nom est ExampleContentHandler. Il crée et exécute ensuite une instruction SQL qui retourne un jeu de données à partir de TestTable1. L'exemple de code obtient ensuite un analyseur SAX pour analyser les données XML.

La méthode showSetters montre comment définir la colonne **xml** avec l’analyseur SAX, ContentHandler et ResultSet. Elle crée tout d’abord un objet SQLXML vide avec la méthode [createSQLXML](../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md) de la classe Connection. Elle obtient ensuite une instance d'un gestionnaire de contenu pour écrire les données dans l'objet SQLXML. L'exemple de code écrit ensuite les données dans TestTable1. Pour finir, l’exemple de code boucle sur les lignes de données du jeu de résultats, et utilise la méthode [getSQLXML](../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md) pour lire les données XML.

La méthode showTransformer montre comment obtenir des données XML à partir d'une table pour les insérer dans une autre table à l'aide de l'analyseur SAX et du transformateur. En premier lieu, elle récupère l'objet SQLXML source à partir de TestTable1. Elle crée ensuite un objet SQLXML de destination vide avec la méthode [createSQLXML](../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md) de la classe Connection. Elle met ensuite à jour l'objet SQLXML de destination et écrit les données XML dans TestTable2. Pour finir, l’exemple de code boucle sur les lignes de données du jeu de résultats, et utilise la méthode [getSQLXML](../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md) pour lire les données XML de TestTable2.

[!code[JDBC#UsingSQLXML1](../../connect/jdbc/codesnippet/Java/sqlxml-data-type-sample_1.java)]

## <a name="see-also"></a>Voir aussi

[Utilisation de types de données &#40;JDBC&#41;](../../connect/jdbc/working-with-data-types-jdbc.md)
