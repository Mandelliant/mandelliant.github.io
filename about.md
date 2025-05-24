---
layout: default
title: About
permalink: /about/
---

<section class="about-header">
    <div class="container">
        <h1>About Me</h1>
        <p class="subtitle">Writer & Technologist</p>
    </div>
</section>

<section class="about-content">
    <div class="container">
        <div class="about-grid">
            <div class="about-main">
                <h2>Professional Background</h2>
                <p>I'm a writer and technologist with expertise in blockchain, cryptocurrencies, product development, data analytics, and digital marketing. My work focuses on making complex technical concepts accessible and engaging for diverse audiences.</p>

                <h2>Areas of Expertise</h2>
                <div class="expertise-grid">
                    <div class="expertise-item">
                        <h3>Blockchain & Crypto</h3>
                        <p>Deep understanding of blockchain technology, cryptocurrencies, and decentralized systems.</p>
                    </div>
                    <div class="expertise-item">
                        <h3>Product Development</h3>
                        <p>Experience in building and scaling successful products with a focus on user needs.</p>
                    </div>
                    <div class="expertise-item">
                        <h3>Data Analytics</h3>
                        <p>Expertise in data-driven decision making and analytics implementation.</p>
                    </div>
                    <div class="expertise-item">
                        <h3>Digital Marketing</h3>
                        <p>Strategic approach to digital marketing and content creation.</p>
                    </div>
                </div>

                <h2>Writing Experience</h2>
                <div class="writing-experience">
                    <div class="experience-item">
                        <h3>Census</h3>
                        <ul>
                            <li><a href="https://blog.getcensus.com/introduction-to-data-driven-lead-scoring-for-sales-marketing-analysts/">Introduction to data-driven lead scoring for sales & marketing analysts</a></li>
                        </ul>
                    </div>
                    <div class="experience-item">
                        <h3>Snowplow Analytics</h3>
                        <ul>
                            <li><a href="https://snowplowanalytics.com/blog/2021/03/11/privacy-updates-ad-blockers-and-the-need-for-1st-party-tracking/">Privacy updates, ad blockers, and the need for 1st-party tracking</a></li>
                            <li><a href="https://snowplowanalytics.com/blog/2019/02/05/how-data-ownership-makes-you-a-more-effective-data-scientist/">How data ownership makes you a more effective data scientist</a></li>
                        </ul>
                    </div>
                    <div class="experience-item">
                        <h3>Blockchannel</h3>
                        <ul>
                            <li><a href="https://medium.com/blockchannel/stop-renting-buy-top-level-domains-with-bob-wallet-16a25acfbd76">Stop renting: buy top-level domains with Bob Wallet</a></li>
                            <li><a href="https://medium.com/blockchannel/sexy-second-level-domains-for-your-substack-with-handshake-8de2155a2f52">Sexy second-level domains for your Substack with Handshake</a></li>
                        </ul>
                    </div>
                </div>
            </div>

            <div class="about-sidebar">
                <div class="contact-card">
                    <h3>Get in Touch</h3>
                    <p>Interested in working together? Feel free to reach out.</p>
                    <a href="mailto:{{ site.email }}" class="button">Email Me</a>
                </div>

                <div class="social-card">
                    <h3>Connect</h3>
                    <div class="social-links">
                        {% for social in site.social %}
                        <a href="https://{{ social.platform }}.com/{{ social.username }}" target="_blank" rel="noopener noreferrer">
                            {{ social.platform | capitalize }}
                        </a>
                        {% endfor %}
                    </div>
                </div>
            </div>
        </div>
    </div>
</section> 