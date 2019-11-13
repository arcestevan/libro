<html>
	<head>
		<meta charset="utf-8">
		<title>DISEÑO RESPONSIVO</title>
		<link rel="stylesheet" type="text/css" href="css/normalize.css" />
		<link rel="stylesheet" type="text/css" href="css/estilos.css">
		<script type="text/javascript" src="js/respond.min.js"></script>

		<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"> 
		<meta name="viewport" content="width=device-width, initial-scale=1.0"> 
		<title>BookBlock: A Content Flip Plugin - Demo 1</title>
		<meta name="description" content="Bookblock: A Content Flip Plugin - Demo 1" />
		<meta name="keywords" content="javascript, jquery, plugin, css3, flip, page, 3d, booklet, book, perspective" />
		<meta name="author" content="Ramirex" />
		<link rel="shortcut icon" href="../favicon.ico"> 
		<link rel="stylesheet" type="text/css" href="css/default.css" />
		<link rel="stylesheet" type="text/css" href="css/bookblock.css" />
		<!-- custom demo style -->
		<link rel="stylesheet" type="text/css" href="css/demo1.css" />
		<script src="js/modernizr.custom.js"></script>
	</head>
	<body>
		<div id="control">
				<a id="bb-nav-first" href="#" >First page</a>
				<a id="bb-nav-prev" href="#" >Previous</a>
				<a id="bb-nav-next" href="#" >Next</a>
				<a id="bb-nav-last" href="#" >Last page</a>
		</div>
		<!-- <div id="bb-bookblock" class="bb-bookblock"> -->
		<div id="bb-bookblock" class="bb-bookblock">
						<div class="bb-item">
							<div id="ima1" alt="image01" class="foto" ></div>
						</div>
						<div class="bb-item">
							<div id="ima2" alt="image01" class="foto" ></div>
						</div>
						<div class="bb-item">
							<div id="ima3" alt="image01" class="foto" ></div>
						</div>
						<div class="bb-item">
							<div id="ima4" alt="image01" class="foto" ></div>
						</div>
						<div class="bb-item">
							<div id="ima5" alt="image01" class="foto" ></div>
						</div>
					</div>
	<!--	<div id="caja">
			<p> LA WEB responsivba nos permite crear contenido adapable para cualquier tipo de dispositivo
			ya sea p o mobil, para ello usamos un archivo css normalize.css y tambien un archivo java script
		 llamado respond.min.js </p>
		</div> -->
		<script src="js/jquery.min.js"></script>
		<script src="js/jquerypp.custom.js"></script>
		<script src="js/jquery.bookblock.js"></script>
		<script>
			var Page = (function() {
				
				var config = {
						$bookBlock : $( '#bb-bookblock' ),
						$navNext : $( '#bb-nav-next' ),
						$navPrev : $( '#bb-nav-prev' ),
						$navFirst : $( '#bb-nav-first' ),
						$navLast : $( '#bb-nav-last' )
					},
					init = function() {
						config.$bookBlock.bookblock( {
							speed : 800,
							shadowSides : 0.8,
							shadowFlip : 0.7
						} );
						initEvents();
					},
					initEvents = function() {
						
						var $slides = config.$bookBlock.children();

						// add navigation events
						config.$navNext.on( 'click touchstart', function() {
							config.$bookBlock.bookblock( 'next' );
							return false;
						} );

						config.$navPrev.on( 'click touchstart', function() {
							config.$bookBlock.bookblock( 'prev' );
							return false;
						} );

						config.$navFirst.on( 'click touchstart', function() {
							config.$bookBlock.bookblock( 'first' );
							return false;
						} );

						config.$navLast.on( 'click touchstart', function() {
							config.$bookBlock.bookblock( 'last' );
							return false;
						} );
						
						// add swipe events
						$slides.on( {
							'swipeleft' : function( event ) {
								config.$bookBlock.bookblock( 'next' );
								return false;
							},
							'swiperight' : function( event ) {
								config.$bookBlock.bookblock( 'prev' );
								return false;
							}
						} );

						// add keyboard events
						$( document ).keydown( function(e) {
							var keyCode = e.keyCode || e.which,
								arrow = {
									left : 37,
									up : 38,
									right : 39,
									down : 40
								};

							switch (keyCode) {
								case arrow.left:
									config.$bookBlock.bookblock( 'prev' );
									break;
								case arrow.right:
									config.$bookBlock.bookblock( 'next' );
									break;
							}
						} );
					};

					return { init : init };

			})();
		</script>
		<script>
				Page.init();
		</script>
	</body>

</html>
