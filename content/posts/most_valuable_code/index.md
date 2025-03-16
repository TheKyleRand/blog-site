+++
date = '2025-03-16T10:54:35-04:00'
draft = false
title = 'The Most Valuable Code in My Suite'
tags = ['AWS', 'Crypto', 'Terraform', 'Trading Bot', 'Crypto Compass', 'Crypto Newspaper']
+++

{{< audio src="audio/most_valuable_code_mad_sci.mp3" >}}

![Featured Image](/images/featured_image.png)

Today, I want to show you the most valuable and expensive code I have in my current suite of crypto projects. I warn you, this is incredibly powerful and dangerous. It controls the entirety of my suite and dictates what the suite is actually capable of. Are you ready?

Here it is:

```hcl
variable "cryptos" {
  description = "List of cryptocurrencies to support"
  type        = list(string)
  default     = ["bitcoin", "ethereum"]
}
```

If you recognize that, you'll notice it's a snippet of Terraform code. It's the variable that dictates what cryptocurrencies are supported by the suite. Want to add another crypto? Just add it to the list. Want to remove one? Just remove it from the list. It really is that simple.

But why is this so valuable?

Well, it's valuable because it allows me to control the suite from a single place. All products in my suite will spin up to support each cryptocurrency from this one variable. I can add or remove a crypto from the list, and the suite will automatically update to support the new crypto. It's a simple change, but it's incredibly powerful. A fleet of resources in AWS, Azure, and GitHub are all controlled by this one variable. Make a modification to that list, and the entire suite is affected. 

How does it work and why did I do this?

I've worked for both a medium-sized company and an extensively large enterprise, and there's always one thing I've done to be successful when writing Terraform modules; make it reusable. Could someone need to modify this variable in the future? Make it a variable. Could two people who need to use this terraform module need a different setting? Make it a variable. It's a very simple principle, but when done right allows for a module that many people have the same necessity for, capable of supporting each use case. By doing this, you can support many people with the same module and cut down on their time to deploy. 

Why mention this now?

Well, when I started building this suite, I realized that if I just made this all about Bitcoin, I would be limiting myself to one audience; Bitcoin enthusiasts. They're great, but there's a much wider audience out there. I would also be limiting the suite's potential. Just analyzing one crypto currency would produce very narrow results. With different cryptocurrencies experiencing different price trends, volatility, and market action, it's important to have a suite that can analyze that and derive results from varying data. 

I need competition within my own suite. It's incredibly important. At this present moment, I have 3 different algorithms each with two trading strategies (only two for now) and all of them run against each other. None of that is powered by AI yet, but it helps show me what's working and what's not. Sure, I also have backtesting systems, but that's boring and only shows action in the past. I want to see what's happening in real time against this most recent time frame of unpredictable downside volatility. What crypto can handle this best? What algorithm handles this best? What trading strategy handles this best? I don't know!... but I'm going to find out.

Some algorithms do better on higher price swings, while some do better with less volatility. Some trading strategies do better with more frequent trades, while others do better with less. These are all factors that are important to know and impossible to determine by just looking at one crypto. While my example code above only contains two coins, the suite supports a much larger list with varying marketcap, trading volume, and price trends. All of this is recorded, stored, and analyzed so that I can make the best decisions for my portfolio.

And I have other Terraform variables that look like this:
```hcl
variable "strategies_per_algo" {
  description = "List of strategies per algorithm"
  default     = ["hyper", "conservative"]
}
```

Now that you've read my explanation above about the "cryptos" variable, this one should be a breeze. It's the same exact concept. I can change the list of strategies per algorithm and the suite will automatically update to support the new strategies. It's a simple change, but it's incredibly powerful. I have plans written down of a flow of a third strategy that employs some parameters to be a hybrid between these two strategies. Once I have that in code, all I have to do is add it to the list and the suite will automatically update to support it. In this case, this variable will control the resources in AWS needed for serverless functions to run the strategies, as well as any necessary resource to support it.

I have a few more variables like this, but I think you get the point.

Every script I have has input parameters to handle dynamic passthroughs of inputs. Nothing gets hardcoded that I think I'll need to change between algorithms, strategies, or cryptocurrencies. These variables are the backbone of the suite. They're the ones that control what the suite is actually capable of. Crypto Compass, the trading bot, AI model pipelines, and even the AI-Generated newspaper are all tied to these variables. Adding a cryptocurrency to that list will spin up each of those four products for that one specific coin. Imagine having a fleet of products you can create in seconds capable of supporting different usecases with different audiences all with just one line of code. That's what this suite is and that's why that Terraform code is the most powerful piece of code in my entire suite.
