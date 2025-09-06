/**
 * Created by lperez on 24/4/2018.
 */

var postURL;
var container;
var loading = '';
loading += '<div class="modal-dialog demo-modal">';
loading += '<div class="modal-content">';
loading += '<div class="modal-body padding-10 text-center">';
loading += '<img src="/img/favicon/BBD-FAVICON-150x150.png" alt="" height="35"/>';
loading += '<h3>Cargando por favor espere</h3>';
loading += '</div>';
loading += '</div>';
loading += '</div>';
var timer;
loadURL = null;
checkURL = null;

$(document).ready(function () {

    container = $('#content');

    $.extend($.validator.messages, {
        required: "Este campo es obligatorio.",
        remote: "Por favor, rellena este campo.",
        email: "Por favor, escribe una dirección de correo válida",
        url: "Por favor, escribe una URL válida.",
        date: "Por favor, escribe una fecha válida.",
        dateISO: "Por favor, escribe una fecha (ISO) válida.",
        number: "Por favor, escribe un número entero válido.",
        digits: "Por favor, escribe sólo dígitos.",
        creditcard: "Por favor, escribe un número de tarjeta válido.",
        equalTo: "Por favor, escribe el mismo valor de nuevo.",
        accept: "Por favor, escribe un valor con una extensión aceptada.",
        maxlength: jQuery.validator.format("Excede la longitud permitida."),
        minlength: jQuery.validator.format("Por favor, no escribas menos de {0} caracteres."),
        rangelength: jQuery.validator.format("Por favor, escribe un valor entre {0} y {1} caracteres."),
        range: jQuery.validator.format("Por favor, escribe un valor entre {0} y {1}."),
        max: jQuery.validator.format("Por favor, escribe un valor menor o igual a {0}."),
        min: jQuery.validator.format("Por favor, escribe un valor mayor o igual a {0}."),
        alphanumeric: jQuery.validator.format("Por favor, no utilice caracteres especiales"),
    });

    /*
     * MASKING
     * Dependency: js/plugin/masked-input/
     */
    if ($(".money,.money2").length) {
        $(".money,.money2").on('paste', function (e) {
            e.preventDefault();
            let paste = (event.clipboardData || window.clipboardData).getData('text');
            parseNum = str => +str.replace(/[^.\d]/g, '');
            e.target.value = parseNum(paste);
            $(this).focus();
        }).on('drop', function (e) {
            e.preventDefault();
        }).on('textInput', function (e) {
            let current_val = e.originalEvent.data;
            if (/^[0-9]*$/.test(current_val) == false)
                e.preventDefault();
        }).maskMoney({thousands: '.', decimal: ',', allowZero: true});
    }

    if ($(".numbersOnly").length) {
        $(".numbersOnly").on('paste', function (e) {
            e.preventDefault();
            let paste = (event.clipboardData || window.clipboardData).getData('text');
            parseNum = str => +str.replace(/[^.\d]/g, '');
            e.target.value = parseNum(paste);
            $(this).focus();
        }).on('drop', function (e) {
            e.preventDefault();
        }).on('textInput', function (e) {
            let current_val = e.originalEvent.data;
            if (/^[0-9]*$/.test(current_val) == false)
                e.preventDefault();
        });
    }

    if ($(".money4").length) {
        $(".money4").on('paste', function (e) {
            e.preventDefault();
            let paste = (event.clipboardData || window.clipboardData).getData('text');
            parseNum = str => +str.replace(/[^.\d]/g, '');
            e.target.value = parseNum(paste);
            $(this).focus();
        }).on('drop', function (e) {
            e.preventDefault();
        }).on('textInput', function (e) {
            let current_val = e.originalEvent.data;
            if (/^[0-9]*$/.test(current_val) == false)
                e.preventDefault();
        }).maskMoney({thousands: '.', decimal: ',', allowZero: true, precision: 4});
    }

    // funcion que permite solo numeros
    $('.input-number').on('input', function () {
        this.value = this.value.replace(/[^0-9]/g, '');
    });

    //Funcion solo permite texto
    $(".txtOnly").keypress(function (event) {
        var regex = new RegExp("^[a-zA-Z]+$");
        var key = String.fromCharCode(!event.charCode ? event.which : event.charCode);
        if (!regex.test(key)) {
            event.preventDefault();
            return false;
        }
    });

    //Funcion solo permite numbro 2.0
    $('.numberOnly').keydown(function (e) {
        // Allow: backspace, delete, tab, escape, enter and .
        if ($.inArray(e.keyCode, [46, 8, 9, 27, 13, 110, 190]) !== -1 ||
            // Allow: Ctrl+A, Command+A
            (e.keyCode === 65 && (e.ctrlKey === true || e.metaKey === true)) ||
            // Allow: Ctrl+A, Command+A
            (e.keyCode === 118 && (e.ctrlKey === true || e.metaKey === true)) ||
            (e.keyCode === 86 && (e.ctrlKey === true || e.metaKey === true)) ||
            // Allow: home, end, left, right, down, up
            (e.keyCode >= 35 && e.keyCode <= 40)) {
            // let it happen, don't do anything
            return;
        }
        // Ensure that it is a number and stop the keypress
        if ((e.shiftKey || (e.keyCode < 48 || e.keyCode > 57)) && (e.keyCode < 96 || e.keyCode > 105)) {
            e.preventDefault();
        }
    });

    //Funcion solo permite numeros sin coma ni punto
    $('.numbersOnly').keydown(function (e) {
        // Allow: backspace, delete, tab, escape, enter and .
        if ($.inArray(e.keyCode, [46, 8, 9, 27, 13]) !== -1 ||
            // Allow: Ctrl+A, Command+A
            (e.keyCode === 65 && (e.ctrlKey === true || e.metaKey === true)) ||
            // Allow: Ctrl+A, Command+A
            (e.keyCode === 118 && (e.ctrlKey === true || e.metaKey === true)) ||
            (e.keyCode === 86 && (e.ctrlKey === true || e.metaKey === true)) ||
            // Allow: home, end, left, right, down, up
            (e.keyCode >= 35 && e.keyCode <= 40)) {
            // let it happen, don't do anything
            return;
        }
        // Ensure that it is a number and stop the keypress
        if ((e.shiftKey || (e.keyCode < 48 || e.keyCode > 57)) && (e.keyCode < 96 || e.keyCode > 105)) {
            e.preventDefault();
        }
    });

    $.datepicker.regional['es'] = {
        closeText: 'Cerrar',
        prevText: '< Ant',
        nextText: 'Sig >',
        currentText: 'Hoy',
        monthNames: ['Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo', 'Junio', 'Julio', 'Agosto', 'Septiembre', 'Octubre', 'Noviembre', 'Diciembre'],
        monthNamesShort: ['Ene', 'Feb', 'Mar', 'Abr', 'May', 'Jun', 'Jul', 'Ago', 'Sep', 'Oct', 'Nov', 'Dic'],
        dayNames: ['Domingo', 'Lunes', 'Martes', 'Miércoles', 'Jueves', 'Viernes', 'Sábado'],
        dayNamesShort: ['Dom', 'Lun', 'Mar', 'Mié', 'Juv', 'Vie', 'Sáb'],
        dayNamesMin: ['Do', 'Lu', 'Ma', 'Mi', 'Ju', 'Vi', 'Sá'],
        weekHeader: 'Sm',
        dateFormat: 'dd/mm/yy',
        firstDay: 1,
        isRTL: false,
        showMonthAfterYear: false,
        yearSuffix: ''
    };

    $.datepicker.setDefaults($.datepicker.regional['es']);


    /*
     * AJAX CALLS
     */

    $.ajaxSetup({
        headers: {
            'X-CSRF-TOKEN': $('meta[name="csrf-token"]').attr('content')
        }
    });

    postURL = function (url, container, data, callback, dataType) {

        try{
            clearInterval(timerToken);
        }catch (e){
        }

        if (dataType === null)
            dataType = "html";

        $.ajax({
                type: "POST",
                url: url,
                data: data,
                dataType: dataType,
                cache: false, // (warning: setting it to false will cause a timestamp and will call the request twice)
                beforeSend: function () {
                    if (container != null) {

                        pagefunction = null;
                        container.removeData().html("");
                        container.html(loading);
                        // Only draw breadcrumb if it is main content material
                        if (container[0] == $("#content")[0]) {
                            $('body').find('> *').filter(':not(' + ignore_key_elms + ')').empty().remove();
                            drawBreadCrumb();
                            $("html").animate({
                                scrollTop: 0
                            }, "fast");
                        }
                    }
                },
                success: function (data) {
                    if (typeof callback == "function") {
                        callback(data);
                    } else {
                        if (container != null) {

                            container.css({
                                opacity: '0.0'
                            }).html(data).delay(50).animate({
                                opacity: '1.0'
                            }, 300);

                            data = null;
                            container = null;
                        }
                    }
                },
                error: function (xhr, status, thrownError, error) {
                    switch (xhr.status) {
                        case 401:
                            swal({
                                type: 'warning',
                                text: 'Su sesión ha expirado',
                                timer: 1000,
                                showConfirmButton: false,
                            }).then(function (d) {
                                window.location.reload();
                            }, function (d) {
                                window.location.reload();
                            });
                            break;
                        case 419:
                            swal({
                                type: 'warning',
                                text: 'Su sesión ha expirado',
                                timer: 1000,
                                showConfirmButton: false,
                            }).then(function (d) {
                                window.location.reload();
                            }, function (d) {
                                window.location.reload();
                            });
                            break;
                        default:
                            data = '<h4 class="ajax-loading-error">' +
                                '<i class="fa fa-warning txt-color-orangeDark"></i>' +
                                '<span class="txt-color-red"> Estimado Cliente </span>' +
                                '</h4>' +
                                '<p class="text-center">En mantenimiento ¡Estamos trabajando para usted!<p>';
                            if (container !== null) {
                                container.css({
                                    opacity: '0.0'
                                }).html(data).delay(50).animate({
                                    opacity: '1.0'
                                }, 300);
                            }
                            break
                    }
                },
                async: true
            }
        );
    }

    // $('input[name="activity"]').change(function () {
    //     var $this = $(this);
    //
    //     url = $this.attr('id');
    //     container = $('.ajax-notifications');
    //
    //     //(url, container);
    //
    //     //clear memory reference
    //     $this = null;
    // });


    checkURL = function () {

        //get the url by removing the hash
        var url = location.href.split('#').splice(1).join('#');
        //BEGIN: IE11 Work Around
        if (!url) {

            try {
                var documentUrl = window.document.URL;
                if (documentUrl) {
                    if (documentUrl.indexOf('#', 0) > 0 && documentUrl.indexOf('#', 0) < (documentUrl.length + 1)) {
                        url = documentUrl.substring(documentUrl.indexOf('#', 0) + 1);

                    }

                }

            } catch (err) {
            }
        }
        //END: IE11 Work Around

        // container = $('#content');
        // Do this if url exists (for page refresh, etc...)
        if (url) {
            // remove all active class
            $('nav li.active').removeClass("active");
            // match the url and add the active class
            $('nav li:has(a[href="' + url + '"])').addClass("active");
            var title = ($('nav a[href="' + url + '"]').attr('title'));

            // change page title from global var
            document.title = (title || document.title);

            // debugState
            if (debugState) {
                root.console.log("Page title: %c " + document.title, debugStyle_green);
            }

            // parse url to jquery
            postURL(url + location.search, container);

        } else {

            $('nav li.active').removeClass("active");

            // grab the first URL from nav
            var $this = $('nav > ul > li:first-child > a[href!="#"]');

            $('nav li:has(a[href="' + $this.attr('href') + '"])').addClass("active");

            postURL($this.attr('href'), container);

            //clear dom reference
            $this = null;

        }

    }

    // // fire this on page load if nav exists
    // if ($('nav').length) {
    //     checkURL();
    // }

    $(document).on('click', 'nav a[href!="#"]', function (e) {
        e.preventDefault();
        var $this = $(e.currentTarget);
        if ($.root_.hasClass('mobile-view-activated')) {
            $.root_.removeClass('hidden-menu');
            $('html').removeClass("hidden-menu-mobile-lock");
            postURL($this.attr('href'), container);
        } else {
            $('nav li.active').removeClass("active");
            $('nav li:has(a[href="' + $this.attr('href') + '"])').addClass("active");
            postURL($this.attr('href'), container);
        }
        $this = null;

    });

    // fire links with targets on different window
    $(document).on('click', 'nav a[target="_blank"]', function (e) {
        e.preventDefault();
        var $this = $(e.currentTarget);

        window.open($this.attr('href'));
    });

    // fire links with targets on same window
    $(document).on('click', 'nav a[target="_top"]', function (e) {
        e.preventDefault();
        var $this = $(e.currentTarget);

        window.location = ($this.attr('href'));
    });

    // all links with hash tags are ignored
    $(document).on('click', 'nav a[href="#"]', function (e) {
        e.preventDefault();
    });

    // DO on hash change
    $(window).on('hashchange', function () {
        checkURL();
    });


    /*
     * INITIALIZE FORMS
     * Description: Select2, Masking, Datepicker, Autocomplete
     */
    runAllForms = function () {

        /*
         * BOOTSTRAP SLIDER PLUGIN
         * Usage:
         * Dependency: js/plugin/bootstrap-slider
         */
        if ($.fn.slider) {
            $('.slider').slider();
        }

        /*
         * SELECT2 PLUGIN
         * Usage:
         * Dependency: js/plugin/select2/
         */
        if ($.fn.select2) {
            $('select.select2').each(function () {
                var $this = $(this),
                    width = $this.attr('data-select-width') || '100%';
                //, _showSearchInput = $this.attr('data-select-search') === 'true';
                $this.select2({
                    //showSearchInput : _showSearchInput,
                    allowClear: true,
                    width: width
                });

                //clear memory reference
                $this = null;
            });
        }

        /*
         * MASKING
         * Dependency: js/plugin/masked-input/
         */
        if ($.fn.mask) {
            $('[data-mask]').each(function () {

                var $this = $(this),
                    mask = $this.attr('data-mask') || 'error...',
                    mask_placeholder = $this.attr('data-mask-placeholder') || 'X';

                $this.mask(mask, {
                    placeholder: mask_placeholder
                });

                //clear memory reference
                $this = null;
            });
        }

        /*
         * AUTOCOMPLETE
         * Dependency: js/jqui
         */
        if ($.fn.autocomplete) {
            $('[data-autocomplete]').each(function () {

                var $this = $(this),
                    availableTags = $this.data('autocomplete') || ["The", "Quick", "Brown", "Fox", "Jumps", "Over", "Three", "Lazy", "Dogs"];

                $this.autocomplete({
                    source: availableTags
                });

                //clear memory reference
                $this = null;
            });
        }

        /*
         * JQUERY UI DATE
         * Dependency: js/libs/jquery-ui-1.10.3.min.js
         * Usage: <input class="datepicker" />
         */
        if ($.fn.datepicker) {
            $('.datepicker').each(function () {

                var $this = $(this),
                    dataDateFormat = $this.attr('data-dateformat') || 'dd.mm.yy';

                $this.datepicker({
                    dateFormat: dataDateFormat,
                    prevText: '<i class="fa fa-chevron-left"></i>',
                    nextText: '<i class="fa fa-chevron-right"></i>',
                });

                //clear memory reference
                $this = null;
            });
        }

        /*
         * AJAX BUTTON LOADING TEXT
         * Usage: <button type="button" data-loading-text="Loading..." class="btn btn-xs btn-default ajax-refresh"> .. </button>
         */
        $('button[data-loading-text]').on('click', function () {
            var btn = $(this);
            btn.button('loading');
            setTimeout(function () {
                btn.button('reset');
                //clear memory reference
                btn = null;
            }, 3000);

        });

        $.extend($.validator.messages, {
            required: "Este campo es obligatorio.",
            remote: "Por favor, rellena este campo.",
            email: "Por favor, escribe una dirección de correo válida",
            url: "Por favor, escribe una URL válida.",
            date: "Por favor, escribe una fecha válida.",
            dateISO: "Por favor, escribe una fecha (ISO) válida.",
            number: "Por favor, escribe un número entero válido.",
            digits: "Por favor, escribe sólo dígitos.",
            creditcard: "Por favor, escribe un número de tarjeta válido.",
            equalTo: "Por favor, escribe el mismo valor de nuevo.",
            accept: "Por favor, escribe un valor con una extensión aceptada.",
            maxlength: jQuery.validator.format("Excede la longitud permitida."),
            minlength: jQuery.validator.format("Por favor, no escribas menos de {0} caracteres."),
            rangelength: jQuery.validator.format("Por favor, escribe un valor entre {0} y {1} caracteres."),
            range: jQuery.validator.format("Por favor, escribe un valor entre {0} y {1}."),
            max: jQuery.validator.format("Por favor, escribe un valor menor o igual a {0}."),
            min: jQuery.validator.format("Por favor, escribe un valor mayor o igual a {0}.")
        });

        /*
         * MASKING
         * Dependency: js/plugin/masked-input/
         */
        if ($(".money,.money2").length) {
            $(".money,.money2").on('paste', function (e) {
                e.preventDefault();
                let paste = (event.clipboardData || window.clipboardData).getData('text');
                parseNum = str => +str.replace(/[^.\d]/g, '');
                e.target.value = parseNum(paste);
                $(this).focus();
            }).on('drop', function (e) {
                e.preventDefault();
            }).on('textInput', function (e) {
                let current_val = e.originalEvent.data;
                if (/^[0-9]*$/.test(current_val) == false)
                    e.preventDefault();
            }).maskMoney({thousands: '.', decimal: ',', allowZero: true});
        }

        if ($(".numbersOnly").length) {
            $(".numbersOnly").on('paste', function (e) {
                e.preventDefault();
                let paste = (event.clipboardData || window.clipboardData).getData('text');
                parseNum = str => +str.replace(/[^.\d]/g, '');
                e.target.value = parseNum(paste);
                $(this).focus();
            }).on('drop', function (e) {
                e.preventDefault();
            }).on('textInput', function (e) {
                let current_val = e.originalEvent.data;
                if (/^[0-9]*$/.test(current_val) == false)
                    e.preventDefault();
            });
        }

        if ($(".money4").length) {
            $(".money4").on('paste', function (e) {
                e.preventDefault();
                let paste = (event.clipboardData || window.clipboardData).getData('text');
                parseNum = str => +str.replace(/[^.\d]/g, '');
                e.target.value = parseNum(paste);
                $(this).focus();
            }).on('drop', function (e) {
                e.preventDefault();
            }).on('textInput', function (e) {
                let current_val = e.originalEvent.data;
                if (/^[0-9]*$/.test(current_val) == false)
                    e.preventDefault();
            }).maskMoney({thousands: '.', decimal: ',', allowZero: true, precision: 4});
        }

        // funcion que permite solo numeros
        $('.input-number').on('input', function () {
            this.value = this.value.replace(/[^0-9]/g, '');
        });

        //Funcion solo permite texto
        $(".txtOnly").keypress(function (event) {
            var regex = new RegExp("^[a-zA-Z_ ]+$");
            var key = String.fromCharCode(!event.charCode ? event.which : event.charCode);
            if (!regex.test(key)) {
                event.preventDefault();
                return false;
            }
        });

        //Funcion solo permite numbro 2.0
        $('.numberOnly').keydown(function (e) {
            // Allow: backspace, delete, tab, escape, enter and .
            if ($.inArray(e.keyCode, [46, 8, 9, 27, 13, 110, 190]) !== -1 ||
                // Allow: Ctrl+A, Command+A
                (e.keyCode === 65 && (e.ctrlKey === true || e.metaKey === true)) ||
                // Allow: Ctrl+A, Command+A
                (e.keyCode === 118 && (e.ctrlKey === true || e.metaKey === true)) ||
                (e.keyCode === 86 && (e.ctrlKey === true || e.metaKey === true)) ||
                // Allow: home, end, left, right, down, up
                (e.keyCode >= 35 && e.keyCode <= 40)) {
                // let it happen, don't do anything
                return;
            }
            // Ensure that it is a number and stop the keypress
            if ((e.shiftKey || (e.keyCode < 48 || e.keyCode > 57)) && (e.keyCode < 96 || e.keyCode > 105)) {
                e.preventDefault();
            }
        });

        //Funcion solo permite numeros sin coma ni punto
        $('.numbersOnly').keydown(function (e) {
            // Allow: backspace, delete, tab, escape, enter and .
            if ($.inArray(e.keyCode, [46, 8, 9, 27, 13]) !== -1 ||
                // Allow: Ctrl+A, Command+A
                (e.keyCode === 65 && (e.ctrlKey === true || e.metaKey === true)) ||
                // Allow: Ctrl+A, Command+A
                (e.keyCode === 118 && (e.ctrlKey === true || e.metaKey === true)) ||
                (e.keyCode === 86 && (e.ctrlKey === true || e.metaKey === true)) ||
                // Allow: home, end, left, right, down, up
                (e.keyCode >= 35 && e.keyCode <= 40)) {
                // let it happen, don't do anything
                return;
            }
            // Ensure that it is a number and stop the keypress
            if ((e.shiftKey || (e.keyCode < 48 || e.keyCode > 57)) && (e.keyCode < 96 || e.keyCode > 105)) {
                e.preventDefault();
            }
        });

        $.datepicker.regional['es'] = {
            closeText: 'Cerrar',
            prevText: '< Ant',
            nextText: 'Sig >',
            currentText: 'Hoy',
            monthNames: ['Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo', 'Junio', 'Julio', 'Agosto', 'Septiembre', 'Octubre', 'Noviembre', 'Diciembre'],
            monthNamesShort: ['Ene', 'Feb', 'Mar', 'Abr', 'May', 'Jun', 'Jul', 'Ago', 'Sep', 'Oct', 'Nov', 'Dic'],
            dayNames: ['Domingo', 'Lunes', 'Martes', 'Miércoles', 'Jueves', 'Viernes', 'Sábado'],
            dayNamesShort: ['Dom', 'Lun', 'Mar', 'Mié', 'Juv', 'Vie', 'Sáb'],
            dayNamesMin: ['Do', 'Lu', 'Ma', 'Mi', 'Ju', 'Vi', 'Sá'],
            weekHeader: 'Sm',
            dateFormat: 'dd/mm/yy',
            firstDay: 1,
            isRTL: false,
            showMonthAfterYear: false,
            yearSuffix: ''
        };

        $.datepicker.setDefaults($.datepicker.regional['es']);

        $('.icon-watch').off('mousedown touchstart').on('mousedown touchstart', function () {
            $(this).siblings('input').attr('type', 'text');
            $(this).data('watch', '1');
            $(this).addClass('fa-eye').removeClass('fa-eye-slash');
        });

        $('.icon-watch').off('mouseup mouseout touchend').on('mouseup mouseout touchend', function () {
            $(this).siblings('input').attr('type', 'password');
            $(this).data('watch', '0');
            $(this).removeClass('fa-eye').addClass('fa-eye-slash');
        });
    }
    /* ~ END: INITIALIZE FORMS */
});

const getMonto = function (m, decimal = 2) {
    let monto = m.replace(/[.,]/g, '');
    monto = parseInt(monto) / Math.pow(10, decimal);
    return monto;
}