---
title: Objet SqlXmlCommand (classes managées SQLXML) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- void ExecuteNonQuery() method
- namespaces property
- Stream ExecuteStream() method
- CommandType property
- RootTag property
- OutputEncoding property
- XmlReader ExecuteXmlReader() method
- Managed Classes [SQLXML], SqlXmlCommand object
- SQLXML Managed Classes, SqlXmlCommand object
- Base Path property
- void ClearParameters() method
- public void ExecuteToStream(Stream outputStream) method
- SqlXmlCommand object
- CommandText property
- XslPath property
- SchemaPath property
- SqlXmlParameter CreateParameter() method
- ClientSideXML property
- CommandStream property
ms.assetid: c1f9e0bb-a89d-4d6a-a96e-289ef516a3a6
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8e7ee45c8d725e233541f4db34796e89327bc11e
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717944"
---
# <a name="sqlxmlcommand-object-sqlxml-managed-classes"></a>Objet SqlXmlCommand (classes managées SQLXML)
  Il s’agit du constructeur de l’objet SqlXmlCommand :  
  
```  
public SqlXmlCommand(string cnString)  
```  
  
 Où `cnString` est la chaîne de connexion ADO ou OLEDB qui identifie le serveur, la base de données et les informations de connexion, par exemple `Provider=SQLOLEDB; Server=(local); database=AdventureWorks; Integrated Security=SSPI"` .  
  
 Dans la chaîne de connexion, le `Provider` doit être SQLOLEDB et le `Data Provider` ne doit pas être inclus dans la chaîne de fournisseur).  
  
 Pour obtenir un exemple fonctionnel, consultez [exécution de requêtes SQL &#40;classes managées SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
## <a name="methods"></a>Méthodes  
 L’objet TheSqlXmlCommand prend en charge plusieurs méthodes, notamment les méthodes suivantes pour exécuter une commande :  
  
 void ExecuteNonQuery ()  
 Exécute la commande, mais ne retourne rien. Cette méthode est utile si vous souhaitez exécuter une commande autre qu'une requête (autrement dit, une commande qui ne retourne rien). L'exécution d'un code de mise à jour (updategram) ou d'un DiffGram qui met à jour des enregistrements mais ne retourne rien est un exemple d'une telle méthode.  
  
 Stream ExecuteStream ()  
 Retourne un nouvel objet de flux. Cette méthode est utile lorsque vous souhaitez que les résultats de la requête vous soient retournés dans un nouveau flux de données. Pour obtenir un exemple fonctionnel, consultez [exécution de requêtes SQL &#40;classes managées SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
 public void ExecuteToStream (Stream outputStream)  
 Écrit les résultats de la requête dans un flux de données existant. Cette méthode est utile lorsque vous avez un flux auquel vous souhaitez ajouter les résultats (par exemple, pour que les résultats de la requête soient écrits dans le System. Web. HttpResponse. OutputStream). Pour obtenir un exemple fonctionnel, consultez [exécution de requêtes SQL &#40;classes managées SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
 XmlReader ExecuteXmlReader ()  
 Retourne un objet XmlReader. Vous pouvez utiliser cette méthode pour manipuler directement des données dans l’objet XmlReader ou pour brancher l’architecture chaînée de System. Xml. Pour plus d'informations, consultez la documentation sur [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework. Pour obtenir un exemple fonctionnel, consultez [exécution de requêtes SQL à l’aide de la méthode ExecuteXmlReader](executing-sql-queries-by-using-the-executexmlreader-method.md).  
  
 L’objet TheSqlXmlCommand prend également en charge les méthodes supplémentaires suivantes :  
  
 SqlXmlParameter, CreateParameter ()  
 Crée un objet SqlXmlParameter. Vous pouvez définir des valeurs pour les paramètres de *nom* et de *valeur* de cet objet. Cette méthode est utile si vous voulez transmettre des paramètres à une commande. Pour obtenir un exemple fonctionnel, consultez [exécution de requêtes SQL &#40;classes managées SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
 void ClearParameters ()  
 Efface le ou les paramètres qui ont été créés pour un objet de commande donné. Cette méthode est utile si vous souhaitez exécuter plusieurs requêtes sur le même objet de commande.  
  
## <a name="properties"></a>Propriétés  
 L’objet SqlXmlCommand prend également en charge les propriétés suivantes :  
  
 ClientSideXml  
 Si la valeur est True, cela indique que la conversion de l'ensemble de lignes en XML doit se produire sur le client et non pas sur le serveur. Cette propriété s'avère utile si vous souhaitez déplacer la charge de performance vers le niveau intermédiaire. La propriété vous permet également d'imbriquer les procédures stockées existantes avec FOR XML pour obtenir une sortie XML.  
  
 SchemaPath  
 Nom du schéma de mappage avec le chemin d'accès au répertoire (par exemple, C:\x\y\MySchema.xml). Cette propriété est utile pour spécifier un schéma de mappage pour des requêtes XPath. Le chemin d'accès spécifié peut être absolu ou relatif. Si le chemin d’accès est relatif, le chemin d’accès de base qui est spécifié dans le chemin d’accès de base est utilisé pour résoudre le chemin d’accès relatif. Si aucun chemin d'accès de base n'est spécifié, le chemin d'accès relatif se rapporte au répertoire en cours. Pour obtenir un exemple fonctionnel, consultez [accès à la fonctionnalité SQLXML dans l’environnement .net](accessing-sqlxml-functionality-in-the-net-environment.md).  
  
 XslPath  
 Nom du fichier XSL avec le chemin d'accès au répertoire. Le chemin d'accès spécifié peut être absolu ou relatif. Si le chemin d’accès est relatif, le chemin d’accès de base qui est spécifié dans le chemin d’accès de base est utilisé pour résoudre le chemin d’accès relatif. Si aucun chemin d'accès de base n'est spécifié, le chemin d'accès relatif se rapporte au répertoire en cours. Pour obtenir un exemple fonctionnel, consultez [application d’une transformation XSL &#40;classes managées SQLXML&#41;](applying-an-xsl-transformation-sqlxml-managed-classes.md).  
  
 Chemin de base  
 Chemin d'accès de base (chemin d'accès à un répertoire). Cette propriété est utile pour résoudre un chemin d’accès relatif qui est spécifié pour un fichier XSL (à l’aide de la propriété XslPath), un fichier de schéma de mappage (à l’aide de la propriété SchemaPath) ou une référence de schéma externe dans un modèle XML (spécifiée à l’aide de l' `mapping-schema` attribut).  
  
 OutputEncoding  
 Spécifie l'encodage pour le flux de données retourné lorsque la commande s'exécute. Cette propriété est utile pour demander un encodage spécifique pour le flux de données retourné. Entre autres, les encodages communément utilisés sont UTF-8, ANSI et Unicode. UTF-8 est l'encodage par défaut.  
  
 Espaces de noms  
 Permet l'exécution de requêtes XPath qui utilisent des espaces de noms. Pour plus d’informations sur les requêtes XPath avec des espaces de noms, consultez [exécution de requêtes XPath avec des espaces de noms &#40;classes managées SQLXML&#41;](executing-xpath-queries-with-namespaces-sqlxml-managed-classes.md). Pour obtenir un exemple fonctionnel, consultez [exécution de requêtes XPath &#40;classes managées SQLXML&#41;](executing-xpath-queries-sqlxml-managed-classes.md).  
  
 RootTag  
 Fournit l'élément racine unique pour XML généré par l'exécution d'une commande. Un document XML valide requiert une balise de niveau racine unique. Si la commande exécutée génère un fragment XML (sans un élément de premier niveau unique), vous pouvez spécifier un élément racine pour les données XML retournées. Pour obtenir un exemple fonctionnel, consultez [application d’une transformation XSL &#40;classes managées SQLXML&#41;](applying-an-xsl-transformation-sqlxml-managed-classes.md).  
  
 CommandText  
 Texte de la commande. Cette propriété est utilisée pour spécifier le texte de la commande que vous souhaitez exécuter. Pour obtenir un exemple fonctionnel, consultez [exécution de requêtes SQL &#40;classes managées SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
 CommandStream  
 Flux de commande. Cette propriété est utile si vous souhaitez exécuter une commande à partir d'un fichier (par exemple, un modèle XML). Lorsque vous utilisez CommandStream, seules les valeurs **« template »**, **« mise à jour »** et **« DiffGram » CommandType** sont prises en charge. Pour obtenir un exemple fonctionnel, consultez [exécution de fichiers modèles à l’aide de la propriété CommandStream](executing-template-files-by-using-the-commandstream-property.md).  
  
 CommandType  
 Identifie le type de commande. Cette propriété est utilisée pour spécifier le type de commande que vous souhaitez exécuter. Les valeurs du tableau ci-dessous déterminent le type de la commande. Pour obtenir un exemple fonctionnel, consultez [accès à la fonctionnalité SQLXML dans l’environnement .net](accessing-sqlxml-functionality-in-the-net-environment.md).  
  
|Valeur|Description|  
|-----------|-----------------|  
|SqlXmlCommandType. SQL|Exécute une commande SQL (par exemple, `SELECT * FROM Employees FOR XML AUTO`).|  
|SqlXmlCommandType. XPath|Exécute une commande XPath (par exemple, `Employees[@EmployeeID=1]`).|  
|SqlXmlCommandType. modèle|Exécute un modèle XML.|  
|SqlXmlCommandType. TemplateFile|Exécute un fichier modèle dans le dossier spécifié.|  
|SqlXmlCommandType. mise à jour|Exécute un code de mise à jour (updategram).|  
|SqlXmlCommandType. DiffGram|Exécute un DiffGram.|  
  
## <a name="see-also"></a>Voir aussi  
 [Objet SqlXmlParameter &#40;les classes managées SQLXML&#41;](sqlxml-managed-classes-sqlxmlparameter-object.md)   
 [Objet SqlXmlAdapter &#40;les classes managées SQLXML&#41;](sqlxml-managed-classes-sqlxmladapter-object.md)  
  
  
