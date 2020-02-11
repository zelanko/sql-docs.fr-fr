---
title: Gestion des connexions et des sessions (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- statefulness [XML for Analysis]
- statelessness [XML for Analysis]
- XML for Analysis, sessions
- states [XML for Analysis]
- XMLA, sessions
- sessions [XML for Analysis]
ms.assetid: b83bb3ff-09be-4fda-9d1d-6248e04ffb21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3bbd5ef006674a61830bf07de31f73c3915b0d4e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62701998"
---
# <a name="managing-connections-and-sessions-xmla"></a>Gestion des connexions et des sessions (XMLA)
  *Conservation* est une condition au cours de laquelle le serveur conserve l’identité et le contexte d’un client entre les appels de méthode. *Abandon* est une condition au cours de laquelle le serveur ne se souvient pas de l’identité et du contexte d’un client après la fin d’un appel de méthode.  
  
 Pour fournir à conservation, XML for Analysis (XMLA) prend en charge des *sessions* qui autorisent l’exécution conjointe d’une série d’instructions. À titre d'exemple, une telle série d'instructions pourrait servir à créer le membre calculé à utiliser dans des requêtes ultérieures.  
  
 En général, les sessions XMLA suivent le comportement suivant énoncé par la spécification OLE DB 2.6 :  
  
-   Les sessions définissent l'étendue contextuelle des transactions et des commandes.  
  
-   Plusieurs commandes peuvent être exécutées dans le contexte d'une seule session.  
  
-   La prise en charge des transactions dans le contexte XMLA s’effectue via des commandes spécifiques au fournisseur envoyées avec la méthode [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) .  
  
 XMLA définit une méthode de prise en charge des sessions dans un environnement Web selon un mode comparable à la méthode employée par le protocole DAV (Distributed Authoring and Versioning) pour implémenter le verrouillage dans un environnement faiblement couplé. Cette implémentation va de pair avec DAV en ce sens que le fournisseur est autorisé à faire expirer les sessions pour divers motifs (par exemple, dépassement de délai ou erreur de connexion). Lorsque les sessions sont prises en charge, les services Web doivent être en mesure de gérer des jeux de commandes interrompus qui doivent être redémarrés.  
  
 La spécification SOAP (Simple Object Access Protocol) du W3C (World Wide Web Consortium) recommande d'utiliser des en-têtes SOAP pour développer de nouveaux protocoles sur les messages SOAP. Le tableau suivant énumère les éléments et les attributs d'en-tête SOAP que XMLA définit pour initialiser, maintenir et fermer une session.  
  
|En-tête SOAP|Description|  
|-----------------|-----------------|  
|BeginSession|Cet en-tête demande au fournisseur de créer une nouvelle session. Le fournisseur doit répondre en construisant une nouvelle session et en retournant l'ID de session dans l'en-tête Session de la réponse SOAP.|  
|SessionId|La zone des valeurs contient l'ID de session qui doit être utilisé dans chaque appel de méthode pour le reste de la session. Le fournisseur spécifié dans la réponse SOAP envoie cette balise et le client doit également envoyer cet attribut avec chaque élément d'en-tête Session.|  
|session|Pour chaque appel de méthode qui se produit dans la session, cet en-tête doit être utilisé, et l'ID de session doit être inclus dans la zone des valeurs de l'en-tête.|  
|EndSession|Pour mettre fin à la session, utilisez cet en-tête. L'ID de session doit être inclus avec la zone des valeurs.|  
  
> [!NOTE]  
>  Un ID de session ne garantit pas qu'une session reste valide. Si la session expire (par exemple, en cas de dépassement de délai ou de perte de la connexion), le fournisseur peut choisir de terminer et d'annuler les actions de cette session. En conséquence, tous les appels de méthode suivants émanant du client sur un ID de session échouent avec une erreur signalant la non validité d'une session. Un client doit gérer cette condition et être en mesure de renvoyer les appels de méthode de session depuis le début.  
  
## <a name="legacy-code-example"></a>Exemple de code existant  
 L'exemple suivant illustre la façon dont les sessions sont prises en charge.  
  
1.  Pour commencer la session, ajoutez un en-tête SOAP BeginSession à l'appel de méthode XMLA sortant du client. Au départ, l'ID de session n'étant pas encore connu, la zone des valeurs est vide.  
  
    ```  
    <SOAP-ENV:Envelope  
       xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
       SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
       <SOAP-ENV:Header>  
          <XA:BeginSession  
             xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
             xsi:type="xsd:int"  
             mustUnderstand="1"/>  
       </SOAP-ENV:Header>  
       <SOAP-ENV:Body>  
          ...<!-- Discover or Execute call goes here.-->  
       </SOAP-ENV:Body>  
    </SOAP-ENV:Envelope>  
    ```  
  
2.  Le message de réponse SOAP du fournisseur comprend l’ID de session dans la zone d’en-tête de retour, \<à l’aide de la balise d’en-tête XMLA SessionID>.  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:Session  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
3.  Pour chaque appel de méthode intervenant au cours de la session, l'en-tête Session doit être ajouté et contenir l'ID de session retourné par le fournisseur.  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:Session  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          mustUnderstand="1"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
4.  Une fois la session terminée, la \<balise EndSession> est utilisée, contenant la valeur d’ID de session associée.  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:EndSession  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          xsi:type="xsd:int"  
          mustUnderstand="1"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Développement avec XMLA dans Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
