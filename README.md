# Stacker-API

## Synopsis

As an introduction to Ajax, this is an application that allows users to enter a coding topic they are interested in and see unaswered questoins in the results
from StackOverflow.  And then the user can find out who the top answerers are for each topic in the other input.  It is a quick
easy way to earn and build reputation on StackOverflow!

**Used for education purposes for Thinkful Bootcamp**

## Code Example

    $.ajax({
            url: "http://api.stackexchange.com/2.2/questions/unanswered",
            data: request,
            dataType: "jsonp", //use jsonp to avoid cross origin issues
            type: "GET",
        })
        .done(function (result) { //this waits for the ajax to return with a succesful promise object
            var searchResults = showSearchResults(request.tagged, result.items.length);

            $('.search-results').html(searchResults);
            //$.each is a higher order function. It takes an array and a function as an argument.
            //The function is executed once for each item in the array.
            $.each(result.items, function (i, item) {
                var question = showQuestion(item);
                $('.results').append(question);
            });
        })
        .fail(function (jqXHR, error) { //this waits for the ajax to return with an error promise object
            var errorElem = showError(error);
            $('.search-results').append(errorElem);
        });

## API Reference

https://api.stackexchange.com/docs

## Link to Website

http://ekeyes694.github.io/stacker-api/
