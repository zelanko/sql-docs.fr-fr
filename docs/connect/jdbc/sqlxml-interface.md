---
title: Interface SQLXML | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7c67be98-efb5-446c-a0e3-ee67c43cb170
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 72cccce89d5e30a92f38b956c8b7996949d3bb46
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "69027698"
---
# <a name="sqlxml-interface"></a>Interface SQLXML

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Le pilote JDBC prend en charge l'API JDBC 4.0, ce qui permet l'introduction de l'interface java.sql.SQLXML. L’interface SQLXML définit des méthodes d’interaction et de manipulation des données XML. Le type de données **SQLXML** correspond au type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **xml**.  
  
L’interface SQLXML fournit des méthodes permettant d’accéder à la valeur XML en tant que **String**, **Reader** ou **Writer**, ou **Stream**. La valeur XML est également accessible à l’aide de **Source** ou via la définition de **Result**, qui sont utilisés avec les API d’analyseurs XML tels que DOM (Document Object Model), SAX (Simple API for XML) et StAX (Streaming API for XML), ainsi que les transformations XSLT et XPath.  
  
## <a name="remarks"></a>Notes  

Le tableau suivant décrit les méthodes définies dans l'interface SQLXML :  
  
|Syntaxe de la méthode|Description de la méthode|  
|-------------------|------------------------|  
|[void free()](https://go.microsoft.com/fwlink/?LinkId=131685)|Cette méthode libère l'objet SQLXML ainsi que les ressources qu'il détient.|  
|[InputStream getBinaryStream()](https://go.microsoft.com/fwlink/?LinkId=131754)|Retourne un flux d'entrée pour la lecture des données de l'objet SQLXML.|  
|[Reader getCharacterStream()](https://go.microsoft.com/fwlink/?LinkId=131755)|Retourne les données **XML** en tant qu’objet java.io.Reader ou flux de caractères.|  
|[T étend Source T getSource(Class\<T> sourceClass)](https://go.microsoft.com/fwlink/?LinkId=131756)|Retourne une **Source** permettant de lire la valeur **XML** spécifiée par cet objet **SQLXML**.<br /><br /> **Remarque :**  La méthode getSource prend en charge les sources suivantes : javax.xml.transform.dom.DOMSource, javax.xml.transform.sax.SAXSource, javax.xml.transform.stax.StAXSource et java.io.InputStream.|  
|[String getString()](https://go.microsoft.com/fwlink/?LinkId=131757)|Retourne une représentation sous forme de chaîne de la valeur **XML** désignée par cet objet SQLXML.|  
|[OutputStream setBinaryStream()](https://go.microsoft.com/fwlink/?LinkId=131758)|Récupère un flux qui permet d’écrire la valeur **XML** représentée par cet objet SQLXML.|  
|[Writer setCharacterStream()](https://go.microsoft.com/fwlink/?LinkId=131759)|Retourne un flux à utiliser pour écrire la valeur **XML** représentée par cet objet SQLXML.|  
|[T étend Result T setResult(Class\<T> resultClass)](https://go.microsoft.com/fwlink/?LinkId=131760)|Retourne un **Result** permettant de définir la valeur **XML** spécifiée par cet objet **SQLXML**.<br /><br /> **Remarque :** La méthode setResult prend en charge les sources suivantes : javax.xml.transform.dom.DOMResult, javax.xml.transform.sax.SAXResult, javax.xml.transform.stax.StaxResult et java.io.OutputStream.|  
|[void setString(String value)](https://go.microsoft.com/fwlink/?LinkId=131762)|Affecte la valeur XML désignée par cet objet SQLXML à la représentation **String** spécifiée.|  
  
Les applications ne peuvent lire et écrire des valeurs XML dans un objet SQLXML qu'une seule fois.  
  
Quand la méthode free() est appelée, l’objet SQLXML devient non valide et n’est plus accessible en lecture ni en écriture. Si l’application tente d’appeler sur cet objet SQLXML une autre méthode que free(), une exception est levée.  
  
L’objet SQLXML cesse d’être accessible en lecture et en écriture lorsque l’application appelle l’une des méthodes getter suivantes : getSource, getCharacterStream, getBinaryStream et getString.  
  
L’objet SQLXML cesse d’être accessible en lecture et en écriture lorsque l’application appelle l’une des méthodes setter suivantes : setResult, setCharacterStream, setBinaryStream et setString.  
  
## <a name="see-also"></a>Voir aussi  

[Prise en charge des données XML](../../connect/jdbc/supporting-xml-data.md)  
