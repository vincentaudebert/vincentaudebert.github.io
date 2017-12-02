---
layout: post
title: React Router - Check params
date:       2017-12-01 10:31:19
summary:    One way to check your route params
categories: javascript react router
---

Hey, it's almost I forgot I had a blog... Sorry private life got ridiculously
busy.

Let's talk about [React Router v4] [1] and its params in the URL.

It might occur that you need to check them. For instance, for my small webapp
HowWindy.com, I need to make sure that the `country` is valid and then that the `area` shortcode is valid too. If any of these two is not, I redirect to not found page.

Note: This example is a very simplified version of my existing code as I was
using [Redux] [2] to update some store state but it would just be noise for this example.

### Router config

Let's have a look at my router config:

{% highlight javascript %} 
ReactDOM.render(
    <Provider store={store}>
        <div>
            <AppContainer />
            <ConnectedRouter history={history}>
                <div>
                    <MenuContainer />
                    <Switch> 
                        <Route 
                            path='/:country/:area/:sport/list'
                            render={props => (
                                <ValidatedRoute 
                                    component={ListContainer}
                                    {...props} 
                                /> 
                            )} 
                        /> 
                        ...
                        <Route 
                            path='/help'
                            component={Help} 
                        /> 
                        <Route 
                            component={NoMatch} 
                        />
                    </Switch>
                </div> 
            </ConnectedRouter>
            <Footer /> 
        </div>
    </Provider>,
    document.getElementById('root')
)
{% endhighlight %}

As you can see, my route is not rendering directly my `<ListContainer>` but it goes through an high order component (HOC) called `<ValidatedRoute>`

### The High Order Component

Let's have a look at the code

{% highlight javascript %}
import React from 'react'
import { Redirect } from 'react-router-dom'

const ValidatedRoute = props => {
    const { country, area } = this.props.match.params;

    // Do tests on country param
    if (country !== 'ValidCountry') {
        return <Redirect exact to={`/not-found`} />
    }

    // Do tests on area param
    if (area !== 'ValidArea') {
        return <Redirect exact to={`/not-found`} />
    }

    return React.createElement(component, this.props)
}

export default ValidatedRoute
{% endhighlight %}

`ValidatedRoute` is rendered first. That way we can catch "on the fly" the
params and make sure they match our conditions and if not we simply render a
`Redirect` component from `react-router-dom` to redirect to a not found url.

Solution inspired by [this thread on Stackoverflow] [3].

  [1]: https://reacttraining.com/react-router/
  [2]: https://redux.js.org/
  [3]: https://stackoverflow.com/a/47006235/2462089
