Notícias - MUNICÍPIO de LISBOA  (function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start': new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0], j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src= 'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f); })(window,document,'script','dataLayer','GTM-KJRRV5N'); WebFontConfig={"custom":{"urls":["\\/typo3temp\\/assets\\/bootstrappackage\\/fonts\\/aa3ec0906afd0cfd6caaeaa5e24a6f0205178f8f3ca5cbdc8e9c1bf04ce69b72\\/webfont.css","\\/typo3conf\\/ext\\/bootstrap\_package\\/Resources\\/Public\\/Fonts\\/bootstrappackageicon.min.css"],"families":["Nunito Sans:200,300,400,500,600,700,800,900","BootstrapPackageIcon"]},"timeout":1000};(function(d){var wf=d.createElement('script'),s=d.scripts[0];wf.src='/typo3conf/ext/bootstrap\_package/Resources/Public/Contrib/webfontloader/webfontloader.js';wf.async=false;s.parentNode.insertBefore(wf,s);})(document); \<iframe src="https://www.googletagmanager.com/ns.html?id=GTM-KJRRV5N" height="0" width="0" style="display:none;visibility:hidden"\>\</iframe\>

 Ir para [conteúdo principal](#page-content) ou [rodapé](#page-footer)

[](#page-content)

* [Cidadania](https://cidadania.lisboa.pt/)
* [Informações e Serviços](https://informacoeseservicos.lisboa.pt/)
* [Transparência](https://transparencia.lisboa.pt/)
* [Revelar](https://revelar.lisboa.pt/)
* [loja lisboa](https://www.lojalisboa.pt/)

[Aviso de mau tempo](https://www.lisboa.pt/atualidade/noticias/detalhe/previsao-de-chuva-intensa-em-lisboa-aviso-amarelo/)

[<img alt="site lisboa" src="/typo3conf/ext/site_lisboa/Resources/Public/Images/logo.svg" height="52" width="192" />](/)

* [Cidade](/cidade)
  * [Ambiente](/cidade/ambiente/entrada)
  * [Bem-estar Animal](/cidade/bem-estar-animal/entrada)
  * [Cultura](/cidade/cultura/entrada)
  * [Desporto](/cidade/desporto/entrada)
  * [Direitos Sociais](/cidade/direitos-sociais/entrada)
  * [Economia e Inovação](/cidade/economia-e-inovacao/entrada)
  * [Educação](/cidade/educacao/entrada)
  * [Habitação](/cidade/habitacao/entrada)
  * [Mobilidade](/cidade/mobilidade/entrada)
  * [Segurança e Prevenção](/cidade/seguranca-e-prevencao/entrada)
  * [Urbanismo](/cidade/urbanismo/entrada)

* [Atualidade](/atualidade/noticias)
  * [Notícias (current)](/atualidade/noticias)
  * [Publicações Periódicas](/atualidade/publicacoes-periodicas)
  * [Reportagens](/atualidade/reportagens)
  * [Dossiês Temáticos](/atualidade/dossies-tematicos)

* [Agenda](/agenda/o-que-fazer)
  * [O que fazer](/agenda/o-que-fazer)
  * [Município](/agenda/municipio)

* [Município](/municipio/entrada)
  * [Entrada](/municipio/entrada)
  * [Câmara Municipal](/municipio/camara-municipal)
  * [Presidente](/municipio/presidente)
  * [Organização Municipal](/municipio/organizacao-municipal)
  * [Assembleia Municipal](/municipio/assembleia-municipal)
  * [Freguesias](/municipio/freguesias)
  * [Relações Internacionais](/municipio/relacoes-internacionais)

* [Pt](/atualidade/noticias)
* En
* ES

[]()

 $.fn.datepicker.defaults.language = 'pt';

 Notícias
==========

[Arquivo de notícias](/atualidade/noticias/arquivo)

Selecionar filtro

[Filtrar notícias](#)

 //var url\_site = "https://www.lisboa.pt/";
var url\_site = window.location.origin;
var url\_page = "https://www.lisboa.pt/atualidade/noticias/";
var url\_page\_en = "https://www.lisboa.pt/en/daily-news/news/";
var url\_page\_fr = "https://www.lisboa.pt/fr/atualidade/nouvelles/";
var url\_php = "/typo3conf/ext/dmc\_tables\_extend/Classes/Noticias/noticias.php";
var category\_class;
var category\_id;
var page\_number; $(function () { $('[data-toggle="tooltip"]').tooltip()
}) function reiniciar() { $( ".news-list-view" ).fadeOut( 800 ); history.pushState({}, null, url\_page); page\_number = null; limpar\_caixas(); $('#cxProcurar').val(''); noticias\_iniciais(); setTimeout(function(){ $( ".news-list-view" ).fadeIn( 800 ); }, 2000);
} function limpar\_caixas() { $(".filters-date").find('option:eq(0)').prop('selected', true); $(".filters-cat").find('option:eq(0)').prop('selected', true); $(".filters-zone").find('option:eq(0)').prop('selected', true); $("#news\_calendar").val(''); $("#news\_calendar").prop('disabled', false); $(".select-costum").addClass("select-default"); $(".select-costum").removeClass("select-bold"); $('#delCat').remove();
} function menu\_pesquisa() { var inicio = "inicio"; jQuery.ajax({ url: url\_site + url\_php, type: "post", data: { categorias: inicio, lingua:pageURL}, cache: true, success: function(html){ $("#filter-page").append(html); if (localStorage.length \>0) { if (localStorage.getItem("procurar\_palavra\_chave") != null) { $("#cxProcurar").val(localStorage.getItem("procurar\_palavra\_chave")); procurar(); } else{ if (localStorage.getItem("pesquisar\_temas") != null) { $('.filters-cat option[value=' + localStorage.getItem("pesquisar\_temas")+ ']').prop('selected', true); } if (localStorage.getItem("pesquisar\_zonas") != null) { $('.filters-zone option[value=' + localStorage.getItem("pesquisar\_zonas")+ ']').prop('selected', true); } if (localStorage.getItem("pesquisar\_news\_calendar\_result") != null) { $("#news\_calendar").val(localStorage.getItem("pesquisar\_news\_calendar\_result")); } if (localStorage.getItem("pesquisar\_news\_dates") != null) { $('.filters-date option[value=' + localStorage.getItem("pesquisar\_news\_dates")+ ']').prop('selected', true); } pesquisar(); } } else{ if (pageURL\_language.indexOf("/cat/") \>= 0){ pesquisar\_categoria(); } else{ noticias\_iniciais(); } } $(".filters-date").change(function() { $('#cxProcurar').val(''); $('#news\_calendar').val(''); var news\_dates = $(".filters-date :selected").index(); if(news\_dates != 0) { $("#news\_calendar").prop('disabled', true); } else{ $("#news\_calendar").prop('disabled', false); } page\_number = null; history.pushState({}, null, url\_page); pesquisar(); }); $(".filters-cat").change(function() { $('#cxProcurar').val(''); page\_number = null; history.pushState({}, null, url\_page); pesquisar(); }); $(".filters-zone").change(function() { $('#cxProcurar').val(''); page\_number = null; history.pushState({}, null, url\_page); pesquisar(); }); //$("#search\_news").click(function() { //pesquisar(); //}); $(".select-costum").change(function() { var val = $(this).val(); if(val == "all") { $(this).addClass("select-default"); $(this).removeClass("select-bold"); $('#delCat').remove(); } else { $(this).removeClass("select-default"); $(this).addClass("select-bold"); if($(this).parent().find('#delCat').length == 0) { $(this).parent().append('\<span id="delCat" class="icon-close" style="display: inline-block;" aria-hidden="true"\>\</span\>'); } } $(".icon-close").click(function() { $(this).prev('.select-costum').addClass("select-default"); $(this).prev('.select-costum').removeClass("select-bold"); $(this).parent().find('option:eq(0)').prop('selected', true); if($(this).parent().hasClass( "filters-date" ) ) { $("#event\_calendar").prop('disabled', false); } $(this).remove(); pesquisar(); }); }); var search\_box = document.getElementById("cxProcurar"); search\_box.addEventListener("keydown", function (e) { if (e.keyCode === 13) { //checks whether the pressed key is "Enter" page\_number = null; history.pushState({}, null, url\_page); procurar(e); } }); $("#btnProcurar").click(function() { page\_number = null; history.pushState({}, null, url\_page); procurar(); }); } });
} function noticias\_iniciais() { var noticias\_inicio = "inicio"; jQuery.ajax({ url: url\_site + url\_php, type: "post", data: { inicio: noticias\_inicio, lingua:pageURL, page:page\_number}, cache: true, success: function(html){ $(".news-list-view").html(html); $( ".page-item a" ).click(function() { page\_number = $(this).attr("href"); page\_number = page\_number.substr(page\_number.indexOf("?page=") + 6); window.history.pushState("", "", '?page=' + page\_number); $('html,body').animate({scrollTop:$(".news-list-view").offset().top}, 500); noticias\_iniciais(); return false; }); } }); } function procurar() { var palavra\_chave = $("#cxProcurar").val(); localStorage.setItem("procurar\_palavra\_chave", palavra\_chave); jQuery.ajax({ url: url\_site + url\_php, type: "post", data: { palavra: palavra\_chave, lingua:pageURL, page:page\_number }, cache: true, success: function(html){ $(".news-list-view").html(html); limpar\_caixas(); $( ".page-item a" ).click(function() { page\_number = $(this).attr("href"); page\_number = page\_number.substr(page\_number.indexOf("?page=") + 6); window.history.pushState("", "", '?page=' + page\_number); $('html,body').animate({scrollTop:$(".news-list-view").offset().top}, 500); procurar(); return false; }); $( "#clean\_filters" ).click(function() { reiniciar(); }); } });
} function pesquisar() { var categoria\_sistema = ""; var local = ""; var total\_categorias = ""; var news\_calendar = ""; var news\_dates\_result = ""; var categoria\_sistema\_result = ""; var local\_result = ""; var total\_categorias\_result = ""; var news\_calendar\_result = $( "#news\_calendar" ).val(); if(news\_calendar\_result != 0) { news\_calendar = news\_calendar\_result.replace(/-/g, ''); localStorage.setItem("pesquisar\_news\_calendar\_result", news\_calendar\_result); } var news\_dates = $(".filters-date :selected").val(); if(news\_dates != "all") { news\_dates\_result = $(".filters-date :selected").text(); localStorage.setItem("pesquisar\_news\_dates", news\_dates); } var categoria\_escolhida = $(".filters-cat :selected").index(); if(categoria\_escolhida != 0) { categoria\_sistema = $(".filters-cat :selected").val(); categoria\_sistema\_result = $(".filters-cat :selected").text(); localStorage.setItem("pesquisar\_temas", categoria\_sistema); } var categoria\_escolhida = $(".filters-zone :selected").index(); if(categoria\_escolhida != 0) { local = $(".filters-zone :selected").val(); local\_result = $(".filters-zone :selected").text(); localStorage.setItem("pesquisar\_zonas", local); } if(categoria\_sistema != 0) { total\_categorias = categoria\_sistema; total\_categorias\_result = categoria\_sistema\_result; } if(local != 0) { if(total\_categorias != 0) { total\_categorias = total\_categorias + ',' + local; total\_categorias\_result = total\_categorias\_result + ', ' + local\_result; } else{ total\_categorias = local; total\_categorias\_result = local\_result; } } if(total\_categorias != 0) { if(news\_calendar != 0) { jQuery.ajax({ url: url\_site + url\_php, type: "post", data: { date: news\_calendar, total: total\_categorias, lingua:pageURL, date\_result: news\_calendar\_result, total\_result: total\_categorias\_result, page:page\_number }, cache: true, success: function(html){ $(".news-list-view").html(html); $( ".page-item a" ).click(function() { page\_number = $(this).attr("href"); page\_number = page\_number.substr(page\_number.indexOf("?page=") + 6); window.history.pushState("", "", '?page=' + page\_number); $('html,body').animate({scrollTop:$(".news-list-view").offset().top}, 500); pesquisar(); return false; }); $( "#clean\_filters" ).click(function() { reiniciar(); $(".icon-close").remove(); }); } }); } else if(news\_dates != "all") { jQuery.ajax({ url: url\_site + url\_php, type: "post", data: { dates: news\_dates, total: total\_categorias, lingua:pageURL, dates\_result: news\_dates\_result, total\_result: total\_categorias\_result, page:page\_number }, cache: true, success: function(html){ $(".news-list-view").html(html); $( ".page-item a" ).click(function() { page\_number = $(this).attr("href"); page\_number = page\_number.substr(page\_number.indexOf("?page=") + 6); window.history.pushState("", "", '?page=' + page\_number); $('html,body').animate({scrollTop:$(".news-list-view").offset().top}, 500); pesquisar(); return false; }); $( "#clean\_filters" ).click(function() { reiniciar(); $(".icon-close").remove(); }); } }); } else{ jQuery.ajax({ url: url\_site + url\_php, type: "post", data: { total: total\_categorias, lingua:pageURL, total\_result: total\_categorias\_result, page:page\_number }, cache: true, success: function(html){ $(".news-list-view").html(html); $(".select-costum").change(function() { var val = $(this).val(); if(val == "all") { $(this).addClass("select-default"); $(this).removeClass("select-bold"); } else { $(this).removeClass("select-default"); $(this).addClass("select-bold"); } }); $( ".page-item a" ).click(function() { page\_number = $(this).attr("href"); page\_number = page\_number.substr(page\_number.indexOf("?page=") + 6); window.history.pushState("", "", '?page=' + page\_number); $('html,body').animate({scrollTop:$(".news-list-view").offset().top}, 500); pesquisar(); return false; }); $( "#clean\_filters" ).click(function() { reiniciar(); $(".icon-close").remove(); }); } }); } } else{ if(news\_calendar != 0) { jQuery.ajax({ url: url\_site + url\_php, type: "post", data: { date: news\_calendar, lingua:pageURL, date\_result: news\_calendar\_result, page:page\_number }, cache: true, success: function(html){ $(".news-list-view").html(html); $( ".page-item a" ).click(function() { page\_number = $(this).attr("href"); page\_number = page\_number.substr(page\_number.indexOf("?page=") + 6); window.history.pushState("", "", '?page=' + page\_number); $('html,body').animate({scrollTop:$(".news-list-view").offset().top}, 500); pesquisar(); return false; }); $( "#clean\_filters" ).click(function() { reiniciar(); $(".icon-close").remove(); }); } }); } else if(news\_dates != "all") { jQuery.ajax({ url: url\_site + url\_php, type: "post", data: { dates: news\_dates, lingua:pageURL, dates\_result: news\_dates\_result, page:page\_number }, cache: true, success: function(html){ $(".news-list-view").html(html); $( ".page-item a" ).click(function() { page\_number = $(this).attr("href"); page\_number = page\_number.substr(page\_number.indexOf("?page=") + 6); window.history.pushState("", "", '?page=' + page\_number); $('html,body').animate({scrollTop:$(".news-list-view").offset().top}, 500); pesquisar(); return false; }); $( "#clean\_filters" ).click(function() { reiniciar(); $(".icon-close").remove(); }); } }); } else{ noticias\_iniciais(); } } } function pesquisar\_categoria() { var sPageURL = $(location).attr('href'); var hash = sPageURL.substring(sPageURL.indexOf('/cat/') + 5); if (hash[hash.length-1] == "/"){ hash =hash.slice(0,-1) } var categoria\_url = hash; jQuery.ajax({ url: url\_site + url\_php, type: "post", data: { parametro: category\_id, parametro\_url: categoria\_url, lingua:pageURL, page:page\_number }, cache: true, success: function(html){ $(".news-list-view").html(html); $('.filters-cat .select-costum').removeClass("select-default"); $('.filters-cat .select-costum').addClass("select-bold"); $( ".list-category a" ).click(function() { category\_class = $(this).attr("class"); category\_id = $(this).attr("id"); sPageURL = sPageURL.replace(hash, category\_class); //window.history.pushState("", "", '?categoria=' + category\_class); window.history.pushState("", "", sPageURL); $('.filters-cat option[value="' + category\_id + '"]').prop('selected', true); pesquisar\_categoria(); return false; }); $( ".page-item a" ).click(function() { page\_number = $(this).attr("href"); page\_number = page\_number.substr(page\_number.indexOf("?page=") + 6); window.history.pushState("", "", '?page=' + page\_number); $('html,body').animate({scrollTop:$(".news-list-view").offset().top}, 500); pesquisar(); return false; }); $( "#clean\_filters" ).click(function() { reiniciar(); }); } }); } function get\_page() { var getUrlParameter = function getUrlParameter(sParam) { var sPageURL = decodeURIComponent(window.location.search.substring(1)), sURLVariables = sPageURL.split('?page'), sParameterName, i; for (i = 0; i \< sURLVariables.length; i++) { sParameterName = sURLVariables[i].split('='); if (sParameterName[0] === sParam) { return sParameterName[1] === undefined ? true : sParameterName[1]; } } }; page\_number = getUrlParameter('page'); } $( document ).ready(function() { pageURL\_language = $(location).attr("href"); if (pageURL\_language.indexOf("/en/") \>= 0){ pageURL = 1; url\_page = url\_page\_en; } else if (pageURL\_language.indexOf("/fr/") \>= 0){ pageURL = 2; url\_page = url\_page\_fr; } else{ pageURL = 0; } if ((pageURL\_language.indexOf("?page=") \>= 0)) { get\_page(); menu\_pesquisa(); } else{ localStorage.removeItem("procurar\_palavra\_chave"); localStorage.removeItem("pesquisar\_news\_calendar\_result"); localStorage.removeItem("pesquisar\_news\_dates"); localStorage.removeItem("pesquisar\_temas"); localStorage.removeItem("pesquisar\_zonas"); localStorage.clear(); menu\_pesquisa(); } });

<img alt="Marca Lisboa" src="/fileadmin/_common/logos_CML/logo_vertical_w.svg" title="" height="531" width="427" />

* Sobre Nós
  ----------

  * [Aplicações móveis](/sobre-nos/aplicacoes-moveis)
  * [Município](/municipio/entrada)
  * [Recrutamento](/municipio/organizacao-municipal/recursos-humanos/recrutamento-e-mobilidade)

* Comunicação
  ----------

  * [Anúncios, Avisos e Editais](https://informacoeseservicos.lisboa.pt/informacao-administrativa/publicacoes-e-notificacoes?category=9&cPage=1)
  * [Boletim Municipal](https://informacoeseservicos.lisboa.pt/informacao-administrativa/boletim-municipal)
  * [Identidade Gráfica](/municipio/camara-municipal/identidade-grafica)
  * [Publicações](/atualidade/publicacoes-periodicas)

* Acesso Rápido
  ----------

  * [Agenda Municipal](/agenda/municipio)
  * [Diretório da Cidade](https://informacoeseservicos.lisboa.pt/contactos/diretorio-da-cidade)
  * [Documentação](https://informacoeseservicos.lisboa.pt/informacao-administrativa/publicacoes-e-notificacoes)
  * [Projetos cofinanciados](https://informacoeseservicos.lisboa.pt/informacao-administrativa/projetos-cofinanciados)

Contactos
----------

800 910 211 (número gratuito)
 218 170 552 (rede fixa nacional)

[Lojas de Atendimento](https://informacoeseservicos.lisboa.pt/contactos/diretorio-da-cidade/cat/atendimento)

[Contacte-nos](https://informacoeseservicos.lisboa.pt/contactos/contacte-nos)

[Atendimento em Língua Gestual Portuguesa (LGP)](https://informacoeseservicos.lisboa.pt/atendimento-em-lingua-gestual-portuguesa)

 if (typeof Visor !== 'undefined' && Visor) { Visor.init({ apptoken: 'mA4DPRwmza', }); }

© Câmara Municipal de Lisboa - [Política de privacidade](https://www.lisboa.pt/politica-de-privacidade), [Termos de utilização](https://www.lisboa.pt/termos-e-condicoes) e [Política de cookies](https://www.lisboa.pt/politica-de-cookies)

Redes sociais:

* [Facebook](https://www.facebook.com/camaradelisboa/)
* [Twitter](http://www.twitter.com/CamaraLisboa)
* [Instagram](http://instagram.com/camara_municipal_lisboa)
* [LinkedIn](https://www.linkedin.com/company/camaralisboa/)
* [YouTube](http://www.youtube.com/user/camaralisboa)

[](#top)

/\*\<![CDATA[\*/
/\*TS\_inlineFooter\*/ var typeOfSlickUids = typeof slickUids; if( typeOfSlickUids != 'undefined' ) { if(Array.isArray(slickUids)){ $(document).ready(function () { for (var i = 0; i \< slickUids.length; i++) { var boolSlickRandomizeX = eval("boolSlickRandomize" + slickUids[i]); //alert(boolSlickRandomizeX); if( boolSlickRandomizeX == true ) { $('#slickid-' + slickUids[i]).randomize(); } } }); } } $(document).ready(function () { if( (typeof obj === "object") && (obj !== null) ) { var sortedKeys = Object.keys(obj).sort(); //alert( sortedKeys[0] ); if(Array.isArray(sortedKeys)){ for (var i = 0; i \< sortedKeys.length; i++) { obj[sortedKeys[i]](); } } } }); jQuery( document ).ready(function() { jQuery('.youtubeVideo').each(function() { if (jQuery(this).width() \< 600){ jQuery(this).addClass( 'small' ); } else{ jQuery(this).removeClass('small') } }); }); jQuery(window).resize(function(){ jQuery('.youtubeVideo').each(function() { if (jQuery(this).width() \< 600){ jQuery(this).addClass( 'small' ); } else{ jQuery(this).removeClass('small') } }); }); /\*]]\>\*/var klaroConfig = {"acceptAll":true,"additionalClass":"","cookieDomain":"","cookieExpiresAfterDays":"365","default":false,"elementID":"klaro","groupByPurpose":true,"hideDeclineAll":false,"hideLearnMore":false,"htmlTexts":true,"lang":"en","mustConsent":false,"poweredBy":"https:\\/\\/consent.websedit.de","privacyPolicy":"https:\\/\\/www.lisboa.pt\\/politica-de-cookies","storageMethod":"cookie","storageName":"klaro","stylePrefix":"klaro we\_cookie\_consent notice--center","testing":false,"translations":{"en":{"consentModal":{"title":"As suas prefer\\u00eancias de privacidade","description":"Qualquer website que visite pode armazenar ou recolher informa\\u00e7\\u00f5es no seu navegador, principalmente na forma de cookies.\\n\\nEsta informa\\u00e7\\u00e3o pode ser sobre si, as suas prefer\\u00eancias, o seu dispositivo ou utilizada para assegurar que o website funciona como previsto. Normalmente a informa\\u00e7\\u00e3o n\\u00e3o identifica diretamente, mas pode proporcionar-lhe uma experi\\u00eancia mais personalizada no website. Pode decidir n\\u00e3o permitir certos tipos de cookies.\\n\\nClique nos diferentes t\\u00edtulos de categorias para saber mais e para alterar as nossas configura\\u00e7\\u00f5es predefinidas. No entanto, saiba que bloquear certos tipos de cookies poder\\u00e1 ter impacto na sua experi\\u00eancia no website e nos servi\\u00e7os que lhe podemos oferecer. \\n"},"privacyPolicy":{"text":"Informa\\u00e7\\u00f5es detalhadas e como pode revogar o seu consentimento a qualquer momento podem ser encontradas na nossa {privacyPolicy}.","name":"Pol\\u00edtica de Cookies"},"consentNotice":{"description":"Utilizamos cookies essenciais ao funcionamento do website que s\\u00e3o autorizados ao iniciar a navega\\u00e7\\u00e3o.\\n\\nCaso n\\u00e3o concorde com a utiliza\\u00e7\\u00e3o de outros cookies, pode alterar a sua configura\\u00e7\\u00e3o e rejeit\\u00e1-los clicando em 'Configura\\u00e7\\u00f5es de Cookies'.\\n\\nSalienta-se que, ao utilizar este sistema, a passagem de consentimento para n\\u00e3o-consentimento n\\u00e3o tem efeito retroactivo, ou seja, n\\u00e3o elimina cookies previamente instalados no dispositivo do Utilizador. Para esse efeito, o Utilizador deve eliminar os cookies atrav\\u00e9s do seu navegador. Para ver como se faz ou saber mais sobre os cookies que usamos, consulte a nossa \\u003Ca href=\\"https:\\/\\/www.lisboa.pt\\/politica-de-cookies\\"\\u003EPol\\u00edtica de Cookies\\u003C\\/a\\u003E.","changeDescription":"Desde a sua \\u00faltima visita, ocorreram altera\\u00e7\\u00f5es nas configura\\u00e7\\u00f5es de privacidade. Por favor, atualize suas configura\\u00e7\\u00f5es.","learnMore":"Configura\\u00e7\\u00f5es de Cookies"},"contextualConsent":{"acceptOnce":"Sim","acceptAlways":"Sempre","description":"Do you want to load external content supplied by {title}?"},"service":{"disableAll":{"title":"Aceitar todos","description":"Tem o direito de revogar o seu consentimento a qualquer momento, individualmente ou em sua totalidade. Se os consentimentos para o processamento de dados forem revogados, os dados que foram legalmente coletados at\\u00e9 a revoga\\u00e7\\u00e3o ainda podem ser processados \\u200b\\u200bpelo provedor."},"optOut":{"title":"(Opt-Out)","description":"This application is loaded by default (but you can disable it)"},"required":{"title":"(essenciais)","description":"This application is always required"},"purpose":"Finalidade","purposes":"Finalidade"},"purposes":{"unknown":"Interno"},"ok":"Aceitar","save":"Guardar defini\\u00e7\\u00f5es","acceptAll":"Aceitar todos","acceptSelected":"Aceitar sele\\u00e7\\u00e3o","decline":"Rejeitar","close":"Fechar","poweredBy":"Provided by websedit"}},"services":[],"purposeOrder":["unknown"]} klaroConfig.services.push({ name: 'other-15', title: 'Cookies de terceiros', description: 'Algumas das nossas páginas incluem conteúdos de sítios externos.', default: false, defaultIfNoConsent: true, required: false, optOut: false, translations: {'en':{'title':'Cookies de terceiros'}}, purposes: ['unknown'], cookies: [['AWSALB', '/', ''], ['AWSALBCORS', '/', '']], callback: ConsentApp.consentChanged, ownCallback:'', gtm:{trigger:'',variable:''} }); klaroConfig.services.push({ name: 'other-14', title: 'Cookies estritamente necessários', description: 'Estes cookies asseguram o bom funcionamento do website, dos serviços e das diferentes ferramentas disponibilizadas no mesmo.', default: true, defaultIfNoConsent: true, required: true, optOut: false, translations: {'en':{'title':'Cookies estritamente necessários'}}, purposes: ['unknown'], cookies: [['klaro', '/', ''], ['fe\_typo\_user', '/', '']], callback: ConsentApp.consentChanged, ownCallback:'', gtm:{trigger:'',variable:''} }); klaroConfig.services.push({ name: 'google-tagmanager-13', title: 'Cookies de funcionalidade e análise', description: 'Estes cookies permitem analisar os seus hábitos de navegação de forma a melhorar o funcionamento do website.', default: false, defaultIfNoConsent: true, required: false, optOut: false, translations: {'en':{'title':'Cookies de funcionalidade e análise'}}, purposes: ['unknown'], cookies: [['\_ga', '/', ''], ['\_gat', '/', ''], ['\_gid', '/', '']], callback: ConsentApp.consentChanged, ownCallback:'', gtm:{trigger:'',variable:''} });
